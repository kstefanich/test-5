# Content Configuration

### &#x20;<a href="#configure-a-specific-synchronization" id="configure-a-specific-synchronization"></a>

You can configure how GitBook should parse your Git repository using the `.gitbook.yaml` file that must rely on the root of your repository.β

previous/page: new-folder/page.md

### &#x20;<a href="#root" id="root"></a>

Path to lookup for your documentation defaults to the root directory of the repository. Here's how you can tell GitBook to look into a `./docs` folder:

**All other options that specify paths will be relative to this root folder**. So if you define root as `./docs/` and then `structure.summary` as `./product/SUMMARY.md`, GitBook will actually look for a file in `./docs/product/SUMMARY.md`.β

### &#x20;<a href="#structure" id="structure"></a>

The structure accepts two properties:β

* **readme**: Your documentation's first page. Its default value is `./README.md`
* **summary**: Your documentation's table of content. Its default value is `./SUMMARY.md`

The value of those properties is a path to the corresponding files. The path is relative to the "root" option. For example, here's how you can tell GitBook to look into a `./product` folder for the first page and summary:

readme: ./product/README.md

summary: ./product/SUMMARY.md

### &#x20;<a href="#summary" id="summary"></a>

The `summary` file is a Markdown file (`.md`) that should have the following structure:

\## Use headings to create page groups like this oneβ

\* \[First page's title]\(page1/README.md)

\* \[Some child page]\(page1/page1-1.md)

\* \[Some other child page]\(part1/page1-2.md)

\* \[Second page's title]\(page2/README.md)

\* \[Some child page]\(page2/page2-1.md)

\* \[Some other child page]\(part2/page2-2.md)

\* \[Yet another page]\(another-page.md)

Providing a custom summary file is optional. By default, GitBook will look for a file named `SUMMARY.md` in your `root` folder if specified in your config file, or at the root of the repository otherwise.

If you don't specify a summary, and GitBook does not find a `SUMMARY.md` file at the root of your docs, GitBook will infer the table of contents from the folder structure and the Markdown files below.β

The summary markdown file is **a mirror of the Table of Contents** of your GitBook space. So even when no summary file is provided during an initial import, GitBook will create one and/or update it whenever you update your content using the GitBook editor.

Due to this, it is not possible to reference the same markdown file twice in your `SUMMARY.md` file, because this would imply that a single page lives at two different URLs in your GitBook space.

### &#x20;<a href="#redirects" id="redirects"></a>

You can create custom redirects of a URL to a page by specifying the path to the corresponding file. The path is relative to the ["root" option](https://docs.gitbook.com/integrations/github#root). For example, here's how you can tell GitBook to redirect users accessing `/help` to the support page:

#### &#x20;<a href="#why-would-you-need-a-redirect" id="why-would-you-need-a-redirect"></a>

You may be migrating your docs from a different service to GitBook. It's common to also restructure some of your content along the process. Assuming you had the following URL in your old docs:

`https://docs.company.com/help`

and that has now moved to `https://docs.company.com/misc/support` on GitBook.

Here's how to include a redirect for that scenario:

The path `misc/support.md` needs to be a real existing path within the repository. It needs to be relative to the current `root` settting in `.gitbook.yaml`. Please don't add any leading slashes. For example, `./misc/support.md` will not work.

Please don't add any leading slashes to the old URL path `help`. For example, `/help` will not work.

Here's how you can deal with a more complex URL for the old path:

With Git, when a file is moved many times, the file is removed and a new one is created. This makes it impossible for GitBook to know that a folder has been renamed for example. Make sure to double-check and eventually add a redirect.
