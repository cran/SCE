# SCE 1.1.3

## Breaking changes (API style)
* Per common R conventions, **all exported function names now use lowercase** (including main constructors `sce()` and `sca()`).
* S3 **class names** are now `"sce"` and `"sca"` (previously `"SCE"` and `"SCA"`). Method names follow (`print.sce`, `predict.sca`, etc.).
* Renamed functions include (non-exhaustive): `model_simulation()`, `sca_tree_predict()`, `sce_model_evaluation()`, `sca_model_evaluation()`, `wilks_importance()`, `sca_importance()`, `rfe_sce()`, `plot_rfe()`, and internal helpers such as `sce_prediction()`, `training_prediction()`, `oob_validation()`, `gof()`, `nse_equation()`, `kge_equation()`, `inference()`.
* **Saved `.RDS` / `.RData` models** created with older versions store the previous class names; assign new classes before using S3 methods, e.g. `class(obj) <- "sce"` or `class(obj) <- "sca"` as appropriate.

## Bug fixes
* `sce(parallel = TRUE)` no longer fails on single-core machines (or when `Ntree == 1`); it now falls back to sequential execution instead of leaving the result vector undefined. The cluster is also released via `on.exit()` so a worker error no longer leaks the cluster.

## Documentation
* Updated `README.md`, tutorial script, and manual pages to match the new function and dataset names.

# SCE 1.1.2

## New Features
* Added `digits` argument for variable importance outputs
  * `Wilks_importance()` and `SCA_importance()` now round `Relative_Importance` to `digits` decimal places (default: 2)
  * S3 methods `importance.SCE()` and `importance.SCA()` accept and forward the `digits` argument

## Documentation
* Updated `man/importance.Rd` to document the `digits` parameter and default
* Updated README examples to demonstrate `importance(..., digits = 2)`

## Compatibility
* Backward compatible; only changes displayed precision of importance values. Adjust `digits` to control rounding

# SCE 1.1.1

## New Features
* Added parameter validation warnings to `evaluate()` S3 methods
  * `evaluate.SCA()` now automatically retrieves predictants from the model object (no need to specify)
  * `evaluate.SCA()` now specifically warns if `Training_data` is provided (not needed for SCA evaluation)
  * `evaluate.SCE()` now automatically retrieves predictants from the model object (no need to specify)
  * Both methods now warn if extra parameters beyond required ones are provided
* Enhanced user experience by providing clear guidance on correct parameter usage

# SCE 1.1.0

## New Features
* Added S3 class system for SCE and SCA objects with dedicated methods
* Implemented `print()`, `summary()`, `predict()`, `importance()`, and `evaluate()` methods for S3 objects
* Added `Plot_RFE()` function for visualizing recursive feature elimination results
* Enhanced backward compatibility - functions now work with both S3 objects and legacy list formats

## Improvements
* Improved parallel processing with proper function exports to cluster
* Enhanced error handling and input validation
* Updated documentation with comprehensive examples using S3 methods
* Consolidated documentation files for better organization

## Bug Fixes
* Resolved S3 method dispatch problems
* Corrected parameter order in `Model_simulation()` and `SCA_tree_predict()` functions

## Documentation
* Updated all .Rd files to use S3 methods in examples
* Added comprehensive README with installation and usage instructions
* Improved function documentation with better examples
* Added cross-references between related functions

## Technical Changes
* Added proper NAMESPACE configuration with S3 method registrations
* Imported required graphics functions (`legend`, `lines`) for plotting
* Enhanced package structure for better maintainability 