# GitHub Pages Hugo Template

This is a [template repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-template-repository) generated from the [Hugo quick start guide](https://gohugo.io/getting-started/quick-start/). To demonstrate the happy path of a first time setup with Actions, it does **not** include a `/.github/workflows` folder. Instead, when you enable Pages, we will recommend a starter worfklow based on analysis of the repository's tech stack. In this case, that will of course be a Hugo workflow.

To get started, click the green "Use this template" button at the top right, or [click here](https://github.com/pages-hugoconf-2022/hugo-pages-template/generate). On that page, you'll choose a repository name and owner (either your user account, or any organization where you're allowed to create repositories). After the repository is genereated, go to the settings tab, and under Pages, select "GitHub Actions" under the dropdown for source:

![ScreenShot 2022-07-09 at 00 20 38](https://user-images.githubusercontent.com/13207348/178091369-b2251a73-800b-492e-9ddd-9cf49a889355.png)

Once that setting is applied, it should now recommend a Hugo workflow, which will look like this:

![ScreenShot 2022-07-09 at 00 05 49](https://user-images.githubusercontent.com/13207348/178090975-07cc8f4e-c80e-474f-a54a-c5bc3d267deb.png)

Click the "Configure" button, and you'll be taken to the editor view to review and commit a file named `/.github/workflows/pages.yml`. Feel free to review the syntax and comments, but the workflow sample should be sufficient to build & deploy this template to GitHub Pages on push to the default branch of your respository. If you commit the file to the default branch, the Action should start running within a few seconds. You can review this by going to the `Actions` tab of your repository (`https://github.com/:owner/:repo/actions`).

Once the workflow run completes, the summary view should show the results and display the URL it was published to. For example:

![ScreenShot 2022-07-09 at 00 13 33](https://user-images.githubusercontent.com/13207348/178091171-32e12751-fb5b-4555-9c5c-22f905c6ab81.png)

**Note**: The workflow queries the GitHub API to determine the URL for the repository, and passes this value to Hugo using the `--baseURL` flag. This is why in the example above the URL shows up as `https://tcbyrd.dev/furry-umbrella`. This should help limit any issues with CSS and other assets being generated with the wrong relative URL, since we're telling Hugo to build based on how we generate URLs for user vs project repos. You can read more about different types of Pages sites in [our documentation](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#types-of-github-pages-sites) but the TL;DR is

- If there's a custom domain on that repo, that takes priority.
- If it's a repo named `:user.github.io` and no custom domain is configured, the URL will match the repository name
- All other URLs will be a path off of the domain assigned to the `:user.github.io` repository, where the path matches the name of the repository.
  - This means if there's a custom domain named `example.com` assigned to the pages site published from your `:user.github.io` repository, project pages will be published on `example.com/:repo-name`

