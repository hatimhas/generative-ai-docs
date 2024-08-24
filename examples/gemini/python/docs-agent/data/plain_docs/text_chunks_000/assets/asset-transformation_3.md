An asset transformer is a Dart command-line app that is invoked with
dart run with at least two arguments: --input, which contains the path to
the file to transform and --output, which is the location where the
transformer code must write its output to.
If the transformer applications finishes with a non-zero exit code, the build
fails with error message explaining that transformation of the asset failed.
Anything written to the [stderr] stream of the process by the transformer is
included in the error message.
