Sometimes you want to create an offline copy of a site that you can take and view even without internet access. Using wget you can make such copy easily:

`wget --mirror --convert-links --adjust-extension --page-requisites --no-parent http://example.org`


**Explanation of the various flags:**

`--mirror` – Makes (among other things) the download recursive.

`--convert-links` – convert all the links (also to stuff like CSS stylesheets) to relative, so it will be suitable for offline viewing.

`--adjust-extension` – Adds suitable extensions to filenames (html or css) depending on their content-type.

`--page-requisites` – Download things like CSS style-sheets and images required to properly display the page offline.

`--no-parent` – When recursing do not ascend to the parent directory. It is useful for restricting the download to only a portion of the site.

Alternatively, the command above may be shortened:

`wget -mkEpnp http://example.org`


*Note: that the last p is part of np (--no-parent) and hence you see p twice in the flags.*
