# NanoRepo ISO release synchronization

This repository is the source of NanoOS ISO release assets. Publishing a GitHub Release with an ISO asset triggers `.github/workflows/publish-iso-metadata.yml`.

The workflow:
1. Runs only on the GitHub `release.published` event (draft releases do not trigger it).
2. Verifies that the release has a tag, public release URL, publication timestamp, and at least one ISO or split-ISO asset.
3. Sends a `nanoos.iso.published` event to NanoOS Website and NanoRepo.
4. The website receiver writes `public/releases/iso-latest.json`. NanoRepo records the event as metadata only; it does not try to build an ISO as a Pacman package.

## Required Actions secrets

Create two fine-grained personal access tokens, each scoped to only its target repository:

- `NANOOS_WEBSITE_DISPATCH_TOKEN`: access to `falconediz911-stack/nanoos-website`, repository permission **Contents: write**.
- `NANOREPO_DISPATCH_TOKEN`: access to `falconediz911-stack/NanoRepo`, repository permission **Contents: write**.

Add both as Actions secrets in this ISO repository. GitHub documents Contents: write as the permission required to create a repository-dispatch event.

Never put either token in a workflow file, commit, issue, or log.

## Activation order

1. Merge the NanoRepo source-event receiver PR into NanoRepo `main`.
2. Merge the website ISO-feed receiver PR into website `main`.
3. Add the two Actions secrets to this ISO repository.
4. Publish a new ISO release with its split ISO files and checksum attached.

The current Beta 21 release is a draft and has no uploaded assets, so it will not trigger this workflow. The current draft remains unchanged.

## Scope

This automation publishes ISO release metadata only. It does not update a Pacman package database. The NanoOS Update client must separately be taught to read the website's ISO feed.
