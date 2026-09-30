# Release checklist

## Before release

- [ ] All issues in the milestone are closed or moved
- [ ] All UI text is localized
- [ ] No stray files in the addon folder (test scenes, debug files, unneeded `.import` files)
- [ ] README and docs cover new features
- [ ] `version` in `plugin.cfg` is bumped
- [ ] `CHANGELOG.md` is updated, with breaking changes clearly marked
- [ ] CI is green on the commit to be tagged

## Testing

- [ ] Install the addon in a fresh project
- [ ] Test on the minimum supported Godot version and the latest stable
- [ ] Open a project with registries saved by the previous release: they load and migrate without data loss
- [ ] Re-save a migrated registry and check the diff only contains the expected format changes
- [ ] Export a project and check that registries are synced in the exported build
- [ ] Run the exported build

## Minor release (`x.Y.0`)

- [ ] Create the release branch from `main`: `git switch -c release/X.Y`
- [ ] Tag on the release branch: `git tag vX.Y.0`
- [ ] Push the branch and the tag: `git push origin release/X.Y vX.Y.0`

## Patch release (`x.y.Z`)

- [ ] Cherry-pick the fixes from `main` onto `release/X.Y`
- [ ] Tag on the release branch: `git tag vX.Y.Z`
- [ ] Push the branch and the tag: `git push origin release/X.Y vX.Y.Z`

> [!IMPORTANT]
> Don't forget to bump the version to the patch one in `plugin.cfg`.

## After release

- [ ] Publish the GitHub release with the changelog entry
- [ ] Minor releases only: highlight the main new features
- [ ] Update the Asset Store and Asset Library listings to match the new `README.md` (and screenshots if the UI changed)
- [ ] Copy the changelog entry into the Asset Store
