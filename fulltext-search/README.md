# Full-text search via Algolia

This template shows how to enable full text search on firebase database elements by using an Algolia hosted search service.

## Functions Code

See file [index.js](functions/index.js) for the code.

The dependencies are listed in [package.json](functions/package.json).

## Sample Database Structure

As an example we'll be using a simple blog structure:

```
/functions-project-12345
    /blog-posts
        /key-123456
            text: "This is my first blog entry..."
        /key-123457
            text: "This is my second blog entry..."
    /search
        /queries
            /key-546789
                query: "first entry"
            /key-078234
                query: "second entry"
        /results
            /key-546789
                hits: [...
            /key-078234
                hits: [...
```

Whenever a new blog post is created or modified a Function sends the content to be indexed to the Algolia instance.
To perform new searches clients add the search query to the realtime database under /search/queries/ which triggers a
Firebase function which performs the search on the Algolia instance. The results are written under the /search/results
tree.
