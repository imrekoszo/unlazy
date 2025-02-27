# unlazy

Importable [clj-kondo](https://github.com/clj-kondo/clj-kondo) configuration that discourages the use of several `clojure.core` functions or some of their arities that do lazy processing.

## Usage

Requires at least `v2025.02.20` of clj-kondo.

Add the following to your `deps.edn`, probably under a dev/test alias (the one you use to lint your code). Unless of course you're looking to re-export this config with your artifact, in which case it should probably go into its top-level deps.

```clojure
imrekoszo/unlazy
{:git/url "https://github.com/imrekoszo/unlazy"
 :git/tag "<see https://github.com/imrekoszo/unlazy/releases>"
 :git/sha "<see https://github.com/imrekoszo/unlazy/releases>"}
```

Alternatively just copy the parts you like into your own config.

## Rationale

Lazy processing is a powerful idea and is built into Clojure from the start. Using these functions is idiomatic and learning them are among the first steps most newcomers to the language take.

They do come with an overhead however which is not generally justified, and their behavior can be confusing in some cases. A great article explaining this is https://clojure-goes-fast.com/blog/clojures-deadly-sin/.

My recommendation is to only use lazy processing where absolutely necessary either for functionality or where it does deliver better performance. Personally I prefer transducers with carefully chosen transducible contexts so I can limit the amount of processing done.
