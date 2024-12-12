# Codeplug Structure Documentation

This repository holds the documented codeplug structures needed to keep qdmr up to date. This documentation is usually not edited by hand but using a emulator and reverse engineering tool called anytone-emu. Although initially designed to emulate AnyTone devices, it can basically emulate every device that uses a serial (USB CDC-ACM) interface. For details on that, have a look at the [anytone-emu repository](https://github.com/dmr-tools/anytone-emu).

The structure of this repository is quiet simple: There is a catalog (`catalog.xml`), defining all devices and their firmware versions and a single xml file defining the codeplug. E.g., `d878uv/v3.04.xml` for the AnyTone AT-D878UV with firmware version 3.04. Although these codeplugs are almost identical between firmware revisions and even between some devices, the codeplug definitions are all independent files. This has a single but important advantage, editing one codeplug does not affect any other codeplug.

This approach however, has a couple of disadvantages. A mistake has to be fixed at several places at once and reverse engineering a new firmware version implies a lot of copying. The latter part, however, is quiet easy by copying the entire file or single elements using `anytone-emu`.

Another disadvantage is, that this scheme makes the collaboration harder. It is likely to produce conflicts if several people work on the same codeplug and thus on the same file. To reduce the amount of additional work due to conflicts in codeplug files, a strict workflow using git is needed.

There are several branches in this repository. Although you will not work on them directly, you need to understand, which branch holds what.

| Branch | Description|
| ------ | ---------- |
| `main` | Main branch, holding the lastest firmware versions of all devices |
| `d868uv` | Main branch for the AT-D868UV and AT-D868UVE, holds the latest firmware version for that device. |
| `d868uv-v2.40` | Branch for the particular firmware version 2.40. Here all pull requests for this FW version land. Once that reverse engineering is somewhat complete, it gets pulled into `d868uv` and finally into `main`. |
| `d578uv2` | Main branch for the AT-D578UV III. Holds the latest firmware version for that device, e.g., 2.08. |
| `d578uv2-v2.05` | Branch for a somewhat older firmware version. |
| `d578uv2-v2.08` | Branch for the firmware version 2.08 for the AT-D578UV III. |
| ... | ... |
