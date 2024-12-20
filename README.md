# Web 2 - Astro Lab Day

**Goal:** To learn how to use Astro Content Collections by building a content-based website.

## Instructions

1. Clone the repository to your local machine.
2. Run `cd hilarious-horizon` to go inside the Astro project directory. Run `npm install` to install the node packages/dependencies required by Astro listed inside the `package.json` file.
3. Run `npm run dev` to start the project.
4. Set up your project pages:

    - `home.astro`
    - `about.astro`
    - `projects/index.astro` - Projects listing page
    - `projects/[id].astro` - Individual project pages dynamic route
    - `blog/index.astro` - Blog listing page
    - `blog/[id].astro` - Individual article pages dynamic route

5. Create a directory called `data` inside the `/src` directory. Inside the data directory, create two directories for the content of your projects and blog. Make sure your content is in Markdown format:

    - `src/data/projects/project-1.md`
    - `src/data/projects/project-2.md`
    - `src/data/projects/project-3.md`

    - `src/data/blog/my-first-article.md`
    - `src/data/blog/my-second-article.md`
    - `src/data/blog/my-third-article.md`

    Feel free to add more projects or blog articles. Use dummy content and check out the Markdown guide [https://www.markdownguide.org/basic-syntax/] to help you with the format. Also check out the Astro documentation on how to create the content [https://docs.astro.build/en/guides/content-collections/#defining-custom-ids]

    Take this opportunity to learn and play around with Markdown.

6. Add the properties to the top of your `.md` documents. Make sure the `id` is unique for every file. Keep it the same as the filename for now:

    **Example:**

    ```md
    ---
    title: My Awesome Project 1
    author: Elmer Balbin
    id: project-1 <!-- This will appear as http://localhost:4321/projects/project-1 -->
    ---

    # Markdown content
    ```

7. Create a `content.config.js` inside your `src/` directory. This file is needed to define your collections. Add your collection loaders into the file. Make sure you point them to their respective directories:

    ```js
    import { defineCollection } from 'astro:content';
    import { glob, file } from 'astro/loaders';

    const blog = defineCollection({
      loader: glob({ pattern: "**/*.md", base: "./src/data/blog" })
    });

    export const collections = { blog };
    ```

8. Add content to all your pages using dummy content. For the **projects** and **blog** landing pages, output their collection titles with a *"Read More"* link for each one that points to their dynamic route. Reference: [https://docs.astro.build/en/guides/content-collections/#using-content-in-astro-templates]

9. The dynamic routes `[id].astro` should show the Markdown content. Reference: [https://docs.astro.build/en/guides/content-collections/#building-for-static-output-default]

10. Create a `Header.astro` and `Footer.astro` component. Add a menu to your header so that's easier to navigate your site.

11. Create layout/s that you can wrap your pages in. Layouts should be added inside the `src/layouts` directory. In most cases, these should hold the structure of your website including the meta tags. Pass the `title` from each page as a prop to the layout file to use for the `<title></title>` head element.

12. Add some styling but don't spend too much time on this. Just make your website look clean... and responsive 🤨

### Reference:

- [https://github.com/elmerdotdev/ciccc-web-2-astro-5-part-2-code-along]

## ⚠️ Important Note

Sometimes when you create or add a new collection, you may have to restart your Astro project. You can do `Ctrl+C` to stop the project, and run `npm run dev` to start it up again.
