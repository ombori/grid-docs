# Contributing to Documentation
The Ombori Grid Documentation is an ever-evolving source of information. Ombori is rapidly changing all the time, and so is the documentation.

As with any project, there will always be sections that are not yet complete, missing, or outdated. This is an unavoidable consequence of the rapid changes that occur.

This guide is here to help you figure out how to improve the documentation for all the situations that might arise.

## Running the documentation locally
The documentation is running on Docsify, which is a simple tool to run documentation. All you have to do is install Docsify locally

```bash
    npm i docsify-cli -g
```

The next step is to clone the repository, and step into the directory on the Terminal.

Once cloning is complete, you can run the documentation locally by running the following command inside the directory:

```bash
    yarn start
```

For simplicity, a `package.json` file is available to this project to launch the documentation. However, this is not mandatory for a Docsify project. 

## Adding Docsify Plugins
This Docsify Installation has several plugins added to it. By default, the Docsify Plugins are added by including a Script Tag; however, for faster loading, all these plugins are added to the same `scripts.js` file you can find at the project's root. 

Every script has a `// [name]` on top of it, to identify the plugin. This can also be used to search in the document.

To then finally include the updated scripts, minify the file into `scripts.min.js`, which is included in the `index.html` file.

## Adding missing information on an existing page
Whenever information is missing from a particular document, and you know the solution, we recommend submitting a small PR to add the missing information. 

Follow these steps to ensure correct adjustment of the documentation:

1. Fork the repository or create a branch if you have permission.
2. Find the file you want to adjust. The file's path is a copy of the URL, but you can also press the "Edit on Github" button on the bottom of every page.
3. Find the place in the file that is missing information. 
4. Add the adjustment to the file, whether this is a single word change, an added sentence, or a change to a whole paragraph.
5. Commit, push, and submit a PR.

Don't try to change too many things at once, especially if they're unrelated to each other. Submit a PR for every change, even if they're in the same file. 
## Adding a page to an existing subject
When you want to expand on a subject already covered in the documentation, you can create a new page within that subject. But of course, in order to be able to keep the structure intact, there can be several steps to do this.

Keep in mind; there can't be *hard* rules about how to structure documentation, and it still boils down to preference in most cases.

- If the subject currently resides in "general", you need to consider if an added page is the right solution or if an added section to the same document is sufficient.
- If you conclude that a new page is required, try to figure out if it needs to move away from General to a standalone directory.
- When you create a new directory, check the next section of this guide about creating a new section.

Whatever is decided, it is crucial to keep simplicity in mind. Don't create new pages that could fit within another page, but also don't bloat pages too much. There's a fine line in-between. 

## Adding images
When you want to add an image to the documentation, always include it in the repository. Follow these steps to make sure the image is optimally included:

- Resize the image as small as possible without losing information.
- Compress the image after resizing. This typically saves another 30-50% of the file size. You could use a tool like [TinyPNG](https://tinypng.com/).
- Add it to the assets directory in the section you're working on.

Now that you have the image in the repository, you can add it to the documentation. This is done using a simple line with a relative path to the image. For example

```markdown
![](/assets/filename.png ":size=400")
```

You can define the default image size in pixels using the `:size=400` flag. By default images are zoomable, but you can also use the `:no-zoom` flag to disable this if it adds no value.
## Formatting
Markdown formatting is important, and this can be done automatically. Especially with Tables!

For this the Visual Studio Code extension [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) is recommended.

## Creating a new documentation section
When you want to create a new documentation section, you can create a new directory.

Rules for a new section:
- The directory name should be short and descriptive.
- The directory name should follow kebab-case.
- The directory should contain a `README.md` file as the introduction to the subject
- The directory should contain a `_sidebar.md` file with links to relevant documentation. Check existing directories for examples. 
- Always add a link back to "all documentation" at the bottom or top of the sidebar.
- Any images that are part of the section should be under `[sectionname]/assets`.
- When adding release notes to a section, add those to a directory called `releasenotes`, then add the release notes to the `README.md` file within that directory. Any images that are part of the release notes should be under `[sectionname]/releasenotes/assets`.

Now that you have an entirely new section, the writing begins. Try to follow the same rules and structure as the rest of the documentation. Stick to logical filenames and directories, split things up if they become too complicated or if they're trying to achieve more than one thing.

## Updating release notes
Every section can have release notes, but they should be written only for "products" or "solutions" the users interact with separately. These release notes should also be structured to be with the rest of the documentation of said product or solution.

### Release Notes Format
There are 2 defined release notes formats. The format is determined by the release schedule. If it is a product the user cannot change the version of, like the Console, then a `YYY-MM-DD` format should be kept. If the user can choose the version, then the version number should be used for the release notes. Check `console release notes` and `queue manager release notes` respectively for examples.

Formatting the Release Notes headers in Markdown should be done as follows:

- Version should have a secondary header, like `## [Version]`
- Sub-headers dividing different sections, like bug/features, or distinctions between categories, should have the 4th header, like `#### [Subheader]`

This header distinction is made to have the sidebar populated accordingly and not show all the sub-headers.

### Adding a new version
When adding a new version, stick to the `release notes format` as described above. There are some rules to follow.

- Always add the newest version on top
- Separate the bugfixes from the features
- Add screenshots to features that can improve the clarity of descriptions
- Put screenshots, or other images, in the `assets` directory in the `releasenotes` directory.
- When a release notes page is getting too long, consider "archiving" older release notes to a separate file and link this from the bottom of the release notes page.

After you've added a new version, it is time to make sure the documentation is no longer outdated. This is, of course, something that should've been scoped before the release; however, now is as good a time as any.

## Keeping the documentation up to date
Code is ever-changing, and with changing code, breaking changes and new features, guides, references, and other documentation will start to get outdated. Therefore, it is essential to check the documentation whenever breaking or major changes are made to something that is documented.

So with the addition of a release note, you will have to check the rest of the documentation for required changes. So whenever a new version, feature, or breaking change is scheduled, go over the documented content.


