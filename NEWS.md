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