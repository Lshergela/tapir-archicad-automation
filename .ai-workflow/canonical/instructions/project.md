# Tapir Archicad Automation project contract

## Repository role

Tapir contains an Archicad Add-On that registers additional JSON commands plus its companion automation
components. Command names, input schemas, response schemas, and Archicad-version guards are public
integration contracts used by external clients such as Archicad Plan Importer.

## Binding contracts

- Register a new Add-On command in the same command group/version model used by `AddOnMain.cpp`, and keep
  its input/response schema synchronized with the implementation and documentation.
- Preserve conditional compilation and API compatibility across supported Archicad 25-29 DevKits.
  Do not infer that compiling against one SDK proves compatibility with the matrix.
- CMake is the build authority. CI generates and builds Debug and RelWithDebInfo on Windows and macOS for
  each supported Archicad version using the matching Graphisoft DevKit.
- Unit or schema checks cannot prove an Archicad mutation. Changes to element creation or placement need
  an explicit live Archicad verification result before they are represented as fully validated.
- Do not change release versioning or publish artifacts unless the request includes a release.

## Verification

Run the narrow local CMake build available for the installed DevKit and rely on the repository CI matrix
for cross-version compilation. Record separately whether live Archicad behavior was exercised.
