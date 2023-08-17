# build.closure

ClojureScript depends on the Google Closure JavaScript Libraries,
but Google does not publish those libraries in a Maven repository.
The github action in this repo generates Maven projects for the
Google Closure Library and, optionally, deploys them.

The Google Closure Libraries are divided into two parts: the main
library and third-party extensions. The main library is Apache
licensed; the third-party extensions have a variety of different
licenses. However, code in the main library depends on the
third-party extensions, not the other way around. See CLJS-418 for
details.

To manage this, we build two JARs, google-closure-library and
google-closure-library-third-party, with the former declaring an
explicit dependency on the latter. This permits consumers to exclude
the third-party libraries (and their various licenses) if they know
they don't need them.

To match this structure, we need to alter the deps.js file that the
Google Closure Compiler uses to resolve dependencies. See CLJS-276
for details.

The last release ZIP made by Google was 20130212-95c19e7f0f5f. To
get newer versions, we have to go to the Git repository.


