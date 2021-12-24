# math

This repo hosts my math writing (currently using `LaTeX` outputted to `pdf`).

## TOC

tba

## Why not a blog with KaTeX?

I've thought about making a math blog using Svelte and SSR KaTeX, but I don't think it's worth the effort. Based on this [🐙🐱 issue](https://github.com/sveltejs/svelte/issues/6651), the clean way to make the blog in Svelte but have compile-time rendering of KaTeX syntax to HTML would be to follow this [🐙🐱 answer](https://github.com/sveltejs/svelte/issues/6651#issuecomment-898951252):

> I don't know solution of how to use it in Svelte dirrectly, but what about using it through [mdsvex](https://github.com/pngwn/MDsveX)? You can use [remark and rehype plugins](https://mdsvex.com/docs#remarkplugins--rehypeplugins) and yes, there is [KaTeX](https://github.com/remarkjs/remark-math/tree/HEAD/packages/rehype-katex).

I'd rather spend time writing math rather than making dependencies work.
