# training-template

This repository is [The Carpentries'][carpentry-site]
template for creating websites for Instructor Training workshops.

1.  Please *do not fork this repository directly on GitHub.*
    Instead, please use [the instructions below](#creating-a-repository)
    to copy this `training-template` repository and customize it for your workshop.

2.  Please *do your work in your repository's `gh-pages` branch*,
    since that is what is
    [automatically published as a website by GitHub][github-project-pages].

3.  Once you are done,
    please **send your repository's URL to [The Carpentries' administrator][contact]**.
    We build the list of workshops on our websites from the data included in your `index.md` page.
    We can only do that if you [customize][customization] that page correctly
    *and* send us a link to your workshop website.

If you run into problems,
or have ideas about how to make this process simpler,
please [get in touch](#getting-and-giving-help).
The pages on [customizing your website][customization],
the [FAQ][faq],
and the [design notes][design] have more detail on what we do and why.

## Creating a Repository

1.  Log in to GitHub.
    (If you do not have an account, you can quickly create one for free.)
    You must be logged in for the remaining steps to work.

2.  On this page (<https://github.com/carpentries/training-template>),
    click on the green "Use this template" button (top right)

    ![screenshot of this repository's GitHub page with an arrow pointing to the the 'use this template' button on the top left](fig/select-github-use-template.png?raw=true)

3.  Select the owner for your new repository.
    (This will probably be you, but may instead be an organization you belong to.)

4.  Choose a name for your workshop website repository.
    This name should have the form `YYYY-MM-DD-ttt-site`,
    e.g., `2016-12-01-ttt-oomza`,
    where `YYYY-MM-DD` is the start date of the workshop.
   For online workshops, choose `online` as `site`.
    In most cases, the Instructor Training Team will tell you
    the name of the repository you should use.

5.  Make sure the repository is public, leave "Include all branches" unchecked, and click on "Create
    repository from template". You will be redirected to your new copy of the workshop template
    respository.

6. Your new website will be rendered at `https://your_username.github.io/YYYY-MM-DD-ttt-site`.


## Customizing Your Website

1.  Go into your newly-created repository,
    which will be at `https://github.com/your_username/YYYY-MM-DD-ttt-site`.
    For example,
    if your username is `gvwilson`,
    the repository's URL will be `https://github.com/gvwilson/2016-12-01-ttt-oomza`.

3.  Ensure you are on the gh-pages branch by clicking on the branch under the drop
    down in the menu bar (see the note below):

    ![](fig/select-gh-pages-branch.png?raw=true)

3.  Edit the header of `index.md` to customize the list of instructors,
    workshop venue, etc.
    You can do this in the browser by clicking on it in the file view on GitHub
    and then selecting the pencil icon in the menu bar:

    ![](fig/edit-index-file-menu-bar.png?raw=true)

    Editing hints are embedded in `index.md`,
    and full instructions are in [the customization instructions][customization].

6.  Alternatively,
    if you are already familiar with Git,
    you can clone the repository to your desktop,
    and edit `index.md` there,
    and push your changes back to the repository.

    ~~~
    git clone -b gh-pages https://github.com/your_username/YYYY-MM-DD-ttt-site
    ~~~

    You should specify `-b gh-pages` to checkout the gh-pages branch because the imported
    repository doesn't have a `master` branch.

    In order to view your changes once you are done editing,
    you must push to your GitHub repository:

    ~~~
    git push origin gh-pages
    ~~~

7.  When you are done editing,
    go to the GitHub Pages URL for your workshop and preview your changes.
    In the example above, this is `https://gvwilson.github.io/2016-12-01-ttt-oomza`.
    The finished page should look [something like this](fig/completed-page.png?raw=true).

8.  Optional: you can now change the `README.md` file in your website's repository, which contains these instructions, so that it contains a short description of your workshop and a link to the training website.

9.  Optional: Add a link to your workshop website on the repository main page in the description/website section (look for the `Edit` button on the right to add).

**Note:**
please do all of your work in your repository's `gh-pages` branch,
since [GitHub automatically publishes that as a website][github-project-pages].

## (Optional) Checking Your Changes Locally

If you want to preview your changes on your own machine before publishing them on GitHub,
you can do so as described below.

1.  Install the software [described below](#installing-software).
    This may require some work,
    so feel free to preview by pushing to the website.

2.  Run the command

    ~~~
    make serve
    ~~~

    and go to <http://0.0.0.0:4000> to preview your site.
    You can also run this command by typing `make serve`
    (if you have Make installed).

3.  Run the command

    ~~~
    make workshop-check
    ~~~

    to check for a few common errors in your workshop's home page.
    (You must have Python 3 installed to do this.)

## (Optional) Linking to Your Page

At the top of your repository on GitHub you'll see

~~~
No description, website, or topics provided. — Edit
~~~

Click 'Edit' and add:

1.  A very brief description of your workshop in the "Description" box (e.g., "Oomza University workshop, Dec. 2016")

2.  The URL for your workshop in the "Website" box (e.g., `https://gvwilson.github.io/2016-12-01-ttt-oomza`)

This will help people find your website if they come to your repository's home page.

## Creating Extra Pages

In rare cases,
you may want to add extra pages to your workshop website.
You can do this by putting either Markdown or HTML pages in the website's root directory
and styling them according to the instructions give in
[the lesson template][lesson-example].
If you do this,
you *must* also edit `_config.yml` to set these three values:

1.  `carpentry` is "cp" (for The Carpentries).
    This determines which logo is loaded.

2.  `title` is the title of your workshop (typically the venue and date).

Note: `carpentry and `email` duplicate information that's in `index.md`,
but there is no way to avoid this
without requiring people to edit both files in the usual case
where no extra pages are created.

## Installing Software

If you want to set up Jekyll
so that you can preview changes on your own machine before pushing them to GitHub,
you must install the software described below.
(Note: Julian Thilo has written instructions for
[installing Jekyll on Windows][jekyll-windows].)

1.  **Ruby**.
    This is included with Linux and macOS;
    the simplest option on Windows is to use [RubyInstaller][ruby-installer].
    You can test your installation by running `ruby --version`.
    For more information,
    see [the Ruby installation guidelines][ruby-install-guide].

2.  **[RubyGems][rubygems]**
    (the package manager for Ruby).
    You can test your installation by running `gem --version`.

3.  **[Jekyll][jekyll]**.
    You can install this by running `gem install jekyll`.

You can check the formatting of your header by running `bin/workshop_check.py`
(which is invoked by `make workshop-check`).
You must have Python 3 installed in order to do this,
and you will also need the [PyYAML][pyyaml] module.

## Getting and Giving Help

We are committed to offering a pleasant setup experience for our learners, Trainers, Instructors and workshop hosts.
If you find bugs in our instructions,
or would like to suggest improvements,
please [file an issue][issues]
or [mail us][email].

[carpentry-site]: https://carpentries.org/
[contact]: mailto:checkout@carpentries.org
[faq]: https://carpentries.github.io/workshop-template/faq/
[github-project-pages]: https://help.github.com/articles/creating-project-pages-manually/
[importer]: http://import.github.com/new
[issues]: https://github.com/carpentries/training-template/issues
[jekyll]: https://jekyllrb.com/
[jekyll-windows]: http://jekyll-windows.juthilo.com/
[lesson-example]: https://carpentries.github.io/lesson-example/
[pyyaml]: https://pypi.python.org/pypi/PyYAML
[ruby-install-guide]: https://www.ruby-lang.org/en/downloads/
[ruby-installer]: http://rubyinstaller.org/
[rubygems]: https://rubygems.org/pages/download/
[self-organized-workshop-form]: https://amy.carpentries.org/forms/self-organised/
[swc-site]: http://software-carpentry.org
[lc-site]: https://librarycarpentry.org
