# Contributing to Documentation
The Ombori Grid Documentation is an ever-evolving source of information. Ombori is rapidly changing all the time, and so is the documentation.

As with any project, there will always be sections that are not yet complete, missing, or outdated. This is an unavoidable consequence of the rapid changes that occur.

This guide is here to help you figure out how to improve the documentation for all the situations that might arise.

## Running the documentation locally
The documentation is running on Docsify. This is a very easy tool to run documentation. All you have to do is install Docsify locally

```bash
    npm i docsify-cli -g
```

Once this is done, you can run the documentation locally by running the following command:

```bash
    yarn start
```

For simplicity, a `package.json` file was added to this project to launch the documentation. However, this is not mandatory for a Docsify project. 

## Adding Docsify Plugins
This Docsify Installation has several plugins added to it. By default, the Docsify Plugins are added by including a Script Tag; however, for faster loading, all these plugins are added to the same `scripts.js` file you can find at the project's root. 
## Adding missing information on an existing page
Whenever information is missing from a particular document, and you know the solution, we recommend submitting a small PR to add the missing information. 

Follow these steps to ensure correct adjustment of the documentation:

1. Fork the repository or create a branch if you have permission.
2. Find the file you want to adjust. The file's path is a copy of the URL, but you can also press the "Edit on Github" button on the bottom of every page.
3. Find the place in the file that is missing information. 
4. Add the adjustment to the file, whether this is a single word change, an added sentence, or a change to a whole paragraph.
5. Commit, push, and submit a PR.

Don't try to change too many things at once. Especially if they're unrelateed to each other. Submit a PR for multiple changes, even if they're in the same file, when they're not related to each other.

## Adding a page to an existing subject
When you want to expand on a subject already covered in the documentation, you can create a new page within that subject. But of course in order to be able to keep the structure intact, there can be several steps to do this.

Keep in mind, there can't be *hard* rules about how to structure documentation, it still boils down to preference in most cases.

- If the subject currently resides in "general", you need to consider if an added page is the right solution, or if an added section to the same document is sufficient.
- If you come to the conclusion a new page is required, try to figure out if it needs to move away from General to a standalone directory.
- When you create a new directory, check the next section of this guide about creating a new section.

Whatever is decided, it is important to keep simplicity in mind. Don't create new pages that could fit within another page, but also don't bloat pages too much. There's a fine line in-between. 

## Creating a new documentation section
When you want to create a new documentation section, you can do so by creating a new directory.

Rules for a new section:
- The directory name should be short and descriptive.
- The directory name should follow kebab-case.
- The directory should contain a `README.md` file as the introduction to the subject
- The directory should contain a `_sidebar.md` file with links to relevant documentation. Check existing directories for examples. 
- Always add a link back to "all documentation" at the bottom or top of the sidebar.
- Any images that are part of the section should be under `[sectionname]/assets`.
- When adding releasenotes to a section, add those to a directory called `releasenotes`, then add the releasenotes to the `README.md` file within that directory. Any images that are part of the releasenotes should be under `[sectionname]/releasenotes/assets`.
