# [Computational Neuroscience Imbizo](https://imbizo.africa)

Website of the best\* neuroscience summer school.

\* according to the super unbiased and totally objective opinion of the organisers

developed by Christopher Brian Currin [[🔗GitHub](https://github.com/ChrisCurrin) | [🌍website](https://chriscurrin.com)]

## Changing **content**

Content is generally stored in `/content` directory. Each subdirectory is generally a page or collection of "posts" or "articles". The `_index.md` file in each subdirectory is the "landing page" for that section.

`.md` files are Markdown files. Markdown is a simple markup language that is easy to read and write. It is converted to HTML by the [Hugo engine](https://gohugo.io)). Read about [Markdown here](https://www.markdownguide.org/basic-syntax/). These files will have headers denoted by a set of `---` at the top. The headers are in YAML format. Read about [YAML here](https://yaml.org/).

Sometimes information is better stored in a data file. For example, the list of speakers is stored in `/data/faculty.yaml`. This is because it is easier to maintain and update than individual docs in a subfolder. The limitation is that the data has expected formats and is not as flexible as a markdown file. Thus, big changes to data needs appropriate changes to the theme.

### Adding faculty

1. add details to `data/faculty.yml`

   e.g.

   ```yaml
   - name: Christopher Currin
     years:
         - "2019"
         - "2020"
         - "Biophysics"
     affiliation: "University of Cape Town"
     link: https://chriscurrin.com
     image: "/images/people/currin.jpg"
   ```

2. add image to `static/images/people/<surname>.jpg`
   - images should be ~ 500x500px and in jpg format. Passing through <https://tinypng.com> is recommended.
   - can be uploaded directly using GitHub web interface.

## Editing the **theme**

The theme is based on [Imbizo website](https://imbizo.africa) and is a `git submodule` in the `/themes` directory - [imbizo-website-base](https://github.com/isicnimbizo/imbizo-website-base).

Dealing with submodules can be a little tricky. The best way to work with them is to clone the project with the `--recurse-submodules` flag. This will clone the theme as well. If you forget to do this, you can run `git submodule update --init --recursive` to clone the theme.

To make changes to the theme, you need to clone the theme repo and make changes there.

1. Then, commit and push the changes to the **theme repo**.

   - Update the modified file references:`git add <filenames>`
   - Commit the changes: `git commit -m "your message"`
   - Push the changes to the remote **theme repo**:`git push origin main`

3. Then, commit and push the changes to **this repo**.
   - Initialize and update the submodule (if you haven’t already): `git submodule update --init --recursive`
   - Navigate to the submodule directory: `cd themes/theme_repo`
   - Fetch the latest changes: `git fetch`
   - Checkout the latest commit: `git checkout main`
   - Pull the latest changes: `git pull origin main`
   - Navigate back to the parent repository: `cd ../..`
   - Update the submodule reference: `git add themes/theme_repo`
   - Commit the changes: `git commit -m "Updated my-submodule to latest commit"`
   - Push the changes to the remote repository: `git push origin main`

In case of an error fetching the submodule: `git submodule update --force --recursive --init --remote`

If you forget to commit and push the theme repo, the changes will not be reflected in this repo. Changes to theme in this repo will be shown as a file that references which version of the submodule to use. **Don't commit a "dirty" change**. _Some of this may only make sense once you start making changes - that's okay!_

An advantage of this approach is a clean separation of concerns. The theme is a separate project and can be used in other projects. The theme is also a submodule, so it can be updated easily and the appropriate version of the theme can be explicitly used.

## Getting started with development

1. clone project to local directory

    ```bash
    git clone --recurse-submodules <url>
    cd isicnimbizo.github.io
    ```

1. start server

    ```bash
    hugo server -D -d public  
    ```

## LICENSE

based on [Kross Hugo theme](https://github.com/themefisher/kross-hugo/) developed by Themefisher.

licensed using [MIT](https://github.com/themefisher/kross-hugo/blob/master/LICENSE)

icons by [Themify](https://themify.me/themify-icons)

slideshows by [Slick](https://kenwheeler.github.io/slick/)
