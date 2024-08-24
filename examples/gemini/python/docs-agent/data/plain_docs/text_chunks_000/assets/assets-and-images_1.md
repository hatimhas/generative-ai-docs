The assets subsection of the flutter section
specifies files that should be included with the app.
Each asset is identified by an explicit path
(relative to the pubspec.yaml file) where the asset
file is located. The order in which the assets are
declared doesn't matter. The actual directory name used
(assets in first example or directory in the above
example) doesn't matter.
During a build, Flutter places assets into a special
archive called the asset bundle that apps read
from at runtime.
