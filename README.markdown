# Jekyll Revision History Plugin

Page/post revision history for Jekyll/Octopress site. 

Git is the only revision control system currently supported.  

This plugin adds a page variable `page.revisions`, which is a list of recent revisions of the post or page. Each revision contains attributes `date`, `author` and `message`. A page variable `page.last_modified_at` is added as well, which equals to `page.revisions[0].date`. 

The sample template file `revision.html` and `recent_updated.html` shows how to use the variable.

## Usage

Put `revision.rb` in `/_plugins/` (for Jekyll) or `/plugins/` (for Octopress) directory. 

Put `revision.html` and `recent_updated.html` in `/_include` (for Jekyll) or `/source/_include` (for Octopress) directory. 

### Revision History

Include `revision.html` somewhere in your layout file:

	{% include revision.html %}

It lists the revision history of the current post/page. You may modify `revision.html` to get the presentation you want.

### Recent Updates

Include `recent_updated.html` somewhere in your layout file:

	{% include recent_updated.html %}

It lists 10 most recent updated pages and posts in your site. You may modify `recent_updated.html` to get the presentation you want.


## Configuration

Add below configuration into `_config.yaml`:

	revision:
	  max_count: 5

`max_count` is the maximum number of revisions to show. Default is 5 if not set.

## Disable

On site generation, this plugin executes `git log` for every document to retrieve revision history. It takes time when there are a lot of posts. You may disable this plugin during local preview by passing `-- --no-revision` to jekyll startup command.

	$ jekyll serve -- --no-revision
