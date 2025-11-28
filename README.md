# Codeplug Structure Documentation

This repository holds the documented codeplug structures needed to keep qdmr up to date. This documentation is usually not edited by hand but using a emulator and reverse engineering tool called anytone-emu. Although initially designed to emulate AnyTone devices, it can basically emulate every device that uses a serial (USB CDC-ACM) interface. For details on that, have a look at the [anytone-emu repository](https://github.com/dmr-tools/anytone-emu).

The structure of this repository is quiet simple: There is a catalog (`catalog.xml`), including all device definitions. E.g. `d878uv/model.xml`. Each model defines its firmware versions and a single xml file defines the actual codeplug. E.g., `d878uv/v3.04.xml` for the AnyTone AT-D878UV with firmware version 3.04. Although these codeplugs are almost identical between firmware revisions and even between some devices, the codeplug definitions are all independent files. This has a single but important advantage, editing one codeplug does not affect any other codeplug.

This approach however, has a couple of disadvantages. A mistake has to be fixed at several places and reverse engineering a new firmware version implies a lot of copying. The latter part, however, is quiet easy by copying the entire file or single elements using `anytone-emu`.

Another disadvantage is, that this scheme makes the collaboration harder. It is likely to produce conflicts if several people work on the same codeplug and thus on the same file. To reduce the amount of additional work due to conflicts in codeplug files, a strict workflow using git is needed:

1. Open an issue and declare on what you are working on.
2. Declare small targets. 
3. Fork the repository, clone it locally and work on that one.
4. Once done, submit a pull request. 
5. Submit frequently to minimize the chance, that your fork diverged.
6. Fetch updates from this repository regulary.

