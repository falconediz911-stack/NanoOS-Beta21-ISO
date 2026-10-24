# NanoOS Gaming Beta 21 — ISO

**Build date:** 2026-10-17  
**Status:** Private beta / testing build  
**Architecture:** x86_64  
**ISO filename:** `nanoos-gaming-2026.10.17-beta21-x86_64.iso`  
**ISO size:** 8,439,661,544 bytes (about 7.86 GiB)

## Download

The ISO is larger than GitHub's regular repository file limit. Download all six split ISO parts from the **Releases** page for this repository, along with `ISO-SHA256.txt`.

After downloading all parts into the same directory, reconstruct the ISO on Linux:

```bash
cat nanoos-gaming-2026.10.17-beta21-x86_64.iso.part-* > nanoos-gaming-2026.10.17-beta21-x86_64.iso
```

Verify the reconstructed image:

```bash
echo "65ee4edc965d53f1c364978325434335fcb469bf8355c09c45de6f8ad26eb361  nanoos-gaming-2026.10.17-beta21-x86_64.iso" | sha256sum -c -
```

Expected result: `nanoos-gaming-2026.10.17-beta21-x86_64.iso: OK`.

## SHA-256

```
65ee4edc965d53f1c364978325434335fcb469bf8355c09c45de6f8ad26eb361  nanoos-gaming-2026.10.17-beta21-x86_64.iso
```

## Testing notes

- This is a beta build intended for testing, not a claim of production readiness.
- Test in a virtual machine with a **disposable virtual disk** first.
- Do not install over a daily-use system or a disk containing important data.
- Report the exact ISO checksum and any reproducible installer or boot issues when providing feedback.

## Reconstructing on Windows

Use a file-joining tool or PowerShell to concatenate the parts in filename order. After reconstruction, verify the ISO's SHA-256 with:

```powershell
Get-FileHash .\nanoos-gaming-2026.10.17-beta21-x86_64.iso -Algorithm SHA256
```
