<p align="center">
 <a href="https://discord.gg/Q3St5fPETd"><img alt="Join Discord" src="https://badgen.net/discord/members/Q3St5fPETd/?icon=discord&label=Join%20the%20TrueNAS%20Community" /></a>
 <a href="https://forums.truenas.com/"><img alt="Join Forums" src="https://badgen.net/badge/Forums/Post%20Now//purple" /></a>
 <a href="https://jira.ixsystems.com"><img alt="File Issue" src="https://badgen.net/badge/Jira/File%20Issue//red?icon=jira" /></a>
</p>

Welcome to the TrueNAS Documentation Repository!
The collected documentation for TrueNAS software, hardware, and TrueCommand is stored here.
These files are used to build the TrueNAS Documentation Hub available at https://www.truenas.com/docs/.

Software documentation is released under the Creative Commons license.

# Technologies

* [CommonMark ](https://spec.commonmark.org/current/) and [HTML](https://www.w3schools.com/html/default.asp) governs the syntax for content files.
* [Hugo](https://gohugo.io/) (extended version) builds the website from the content files and governs the file organization, naming, front matter, and some of the [shortcode](https://gohugo.io/content-management/shortcodes/) syntax.
* The custom [GeekDocs theme](https://geekdocs.de/) provides a bare-bones theme with templates and shortcodes for styling the website and content.
* Specific .css customizations are added on top of GeekDocs in the /static/custom.css, /data/menu/, and /layouts/ files

# Installation and Download Process

1. Download Hugo Extended v0.117.0 from [https://github.com/gohugoio/hugo/releases/](https://github.com/gohugoio/hugo/releases/tag/v0.117.0) and [install](https://gohugo.io/getting-started/installing/ "Install Hugo").
   See these instructions for manually installing the Hugo extended version in WSL: https://sal.as/post/install-hugo-on-wsl/

2. Download this repository.

# Local Build Process

1. Open the downloaded repository within your desired text editor and run Hugo with `hugo serve`. When complete, a local copy of the website is available by entering `//localhost:1313/` in a browser address bar.
2. As changes within your chosen text editor or integrated development environment (IDE) are made, Hugo automatically rebuilds the local copy to include the intended modifications.

# Making File Changes

1. From your desired text editor (VS Code, Sublime Text, Atom, Notepad++, etc), utilize [CommonMark](https://spec.commonmark.org/0.31.2/) or [HTML](https://www.w3schools.com/html/default.asp) commands to input changes.
2. Save any intended changes within the text editor and wait for modifications to appear on the local build.
3. If using GitHub Desktop, ensure that all desired changes have been committed to your working branch prior to creating the final pull request.