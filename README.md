# get-latest-release
Get latest release including draft and prerelease. Return information about release.

<em>Difference to other actions which returns latest release is that, this action get access to hiden draft releases.</em>

## Inputs

### `myToken`

**Required** Token to github repository to get access to hidden releases (draft releases)

### `exclude_types`

Exclude some types of releases separated by `|`. Examples: `draft|prerelease`, `prerelease|release`, `draft`

### `view_top`

Numbers of releases which will be searched. Default value `100`.

### `repo`

Name of the repo without owner's name.

### `owner`
The username of the owner who owns the repo.

## Outputs

### `id`

Founded release Id

### `name`

Founded release name

### `tag_name`

Founded release tag

### `created_at`

Founded release creation date

### `draft`

Founded release draft type flag (boolean: `true`, `false`).

### `prerelease`

Founded release prerelease type flag (boolean: `true`, `false`).

## Example usage
```yaml
steps:
  - uses: actions/checkout@v1
  - name: "call action"
    id: last_release
    uses: Dmagine/get-latest-release@master
    with:
      myToken: ${{ github.token }}
      exclude_types: "release"
      view_top: 1
  - name: "Print result"
    run: |
      echo "id: ${{ steps.last_release.outputs.id }}"
      echo "name: ${{ steps.last_release.outputs.name }}"
      echo "tag_name: ${{ steps.last_release.outputs.tag_name }}"
      echo "created_at: ${{ steps.last_release.outputs.created_atd }}"
      echo "draft: ${{ steps.last_release.outputs.draft }}"
      echo "prerelease: ${{ steps.last_release.outputs.prerelease }}"
```
