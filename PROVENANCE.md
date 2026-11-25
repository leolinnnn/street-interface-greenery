# Bang Na code provenance

[← Code and commands](README.md)

All research functions were selected from the supplied project's `scripts/`
directory. [source_manifest.json](source_manifest.json) records source-file SHA-256
values and the original line ranges of extracted functions.

| Public module | Original script | Changes |
| --- | --- | --- |
| `interface_analysis.py` | `analyze_bangna_interface.py` | Eleven functions copied unchanged; import redirected to the local regression module; area-table path points to the bundled extract |
| `regression.py` | `run_bangna_gvi_regression_analysis.py` | Seven functions extracted; `ModelSpec` annotations replaced by `Any`; numerical bodies unchanged |
| `segmentation_metrics.py` | `calculate_bangna_gvi_deeplab_cityscapes.py` | Three functions and class-label constants copied unchanged; MXNet-dependent inference kept separately |
| `network_metrics.py` | `calculate_bangna_road_space_variables.py` | Seven functions copied unchanged; project-file I/O omitted |
| `poi_diversity.py` | `calculate_bangna_functional_variables.py` | Three functions and category definitions copied unchanged |

The three complete files in [legacy](legacy/README.md) retain the original script
content, normalised to UTF-8/LF. They are supplied for inspection and use with the
original input layout. Their end-to-end image/GIS workflows were not rerun for
this portfolio update.

`run_analysis.py`, tests, input-column extracts and documentation were added for
the portfolio on 29 October 2026. The runner calls the archived study routines;
it is distinct from the earlier compact example written for the portfolio.
The original project files were not modified. The manuscript is by **Zihao Lin and Lei Shao**. Pretrained models and
third-party data retain their original attribution and terms.

## Repository organization

On 17 November 2026, the already-shared code, numerical inputs and figures were
organized as a standalone repository in the local portfolio draft. Calculation
modules, runners and numerical data were preserved; documentation, relative
links and a CI configuration were added or reorganized.

## Local organization review — 25 November 2026

File responsibilities and README navigation were aligned across the research
repositories. `source_manifest.json` is the common source-record entry; its
project-specific schema is retained. Research inputs, archived numerical
values, original figures and engine assets preserve their bytes.
