# Jekyll Revision History Plugin

Adds recent revision history to each page on Jekyll/Octopress site. 

Git is the only revision control system currently supported.  


This plugin adds a page variable `page.revisions`, which is a list of recent revisions of the post or page. Each revision contains attributes `date`, `author` and `message`. The sample template file `revision.html` shows how to use the variable.

## Installation

Put `revision.rb` in `/_plugins/` (for Jekyll) or `/plugins/` (for Octopress) directory. 

Put `revision.html` in `/_include` (for Jekyll) or `/source/_include` (for Octopress) directory. Include it somewhere in your layout file:

	{% include revision.html %}

You may modify `revision.html` to get the presentation you want.

## Configuration

Add below configuration into `_config.yaml`:

	revision:
	  max_count: 5

`max_count` is the maximum number of revisions to show. Default is 5 if not set.

## Disable

On site generation, this plugin executes `git log` for every document to retrieve revision history. It takes time when there are a lot of posts. You may disable this plugin during local preview by passing `-- --no-revision` to jekyll startup command.

	$ jekyll serve -- --no-revision
