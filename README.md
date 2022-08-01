# Git nth last tag

GitHub Action that gets last git tag, or nth tag from the last one.

## Inputs

### `skip` (Optional, default: 0)

How many last commits to skip.

## Outputs

### `tag`

Retrieved tag name.

## Example usage

```yaml
steps:
  - uses: actions/checkout@v3
    with:
      fetch-depth: 0
  # v1.2.3
  # v1.2.4
  # v1.2.5
  # v1.2.6
  # v1.2.7 <------- skip: 3
  # v1.3.0
  # v1.3.1 <------- skip: 1
  # v1.3.2 <------- skip: 0
  - name: Get 4th tag from the last one
    id: gittagskipthree
    uses: pavelsaman/git-nth-last-tag@v1.0.0
    with:
      skip: 3
  - name: Get 2nd tag from the last one
    id: gittagskipone
    uses: pavelsaman/git-nth-last-tag@v1.0.0
    with:
      skip: 1
  - name: Get last tag
    id: gittagskipnone
    uses: pavelsaman/git-nth-last-tag@v1.0.0
  - run: echo ${{ steps.gittagskipthree.outputs.tag }} # v1.2.7
  - run: echo ${{ steps.gittagskipone.outputs.tag }}   # v1.3.1
  - run: echo ${{ steps.gittagskipnone.outputs.tag }}  # v1.3.2
```

---

[![Lint](https://github.com/pavelsaman/git-nth-last-tag/actions/workflows/lint.yml/badge.svg)](https://github.com/pavelsaman/git-nth-last-tag/actions/workflows/lint.yml)
