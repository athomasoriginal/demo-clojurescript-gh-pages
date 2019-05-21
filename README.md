# Deploy ClojureScript to Github Pages

This repo contains demo code for [Blog Post](https://github.com/tkjone/blog/blob/master/src/pages/blog-posts/000-deploy-clojurescript-to-github-pages.md). Live site [here](https://tkjone.github.io/demo-clojurescript-gh-pages/)

## Gotchas

For people who are working through the blog post this demo was written for, there are some issues you might run into. Hopefully this section will help to understand and resolve them.

**dev bundle command returns exception: Could not locate cljs/main\_\_init.class**

If you ran this command

```bash
clj -m cljs.main -d "demo-clojurescript-gh-pages/out"  -c demo.static-website -r
```

You could see an exception like this in your terminal:

```bash
Exception in thread "main" java.io.FileNotFoundException: Could not locate cljs/main__init.class, cljs/main.clj or cljs/main.cljc on classpath.
```

The above command generally means that `clojure` could not find `ClojureScript`. Here are some of the reasons why it might occur and how to resolve the issue:

- You might be running the command from the wrong dir

  Please be sure that you are running the dev bundle command from the root of the project dir and you have a `deps.edn` file living there.

- You might not have ClojureScript installed

  The first time you run the command from the correct dir, it should download ClojureScript from maven. However, there are scenarios where `clj` won't try to download ClojureScript. For example, if `clj` sees a `.cpcache` dir, it will not try to download `ClojureScript` again and alway return the above exception.
