# singleFile.PHP.fileManager

A single PHP file, file manager

`config.php`

After you run files app for the first time, `config` file `_files/config/config.php` will get created with all default configuration options commented out.

```sh
# config.php

<?php

// Uncomment the parameters you want to edit.
return array (
  //'root' => '',
  //'start_path' => false,
  //'username' => '',
  //'password' => '',
  //'load_images' => true,
  //'load_files_proxy_php' => false,
  //'load_images_max_filesize' => 1000000,
  //'image_resize_enabled' => true,
  //'image_resize_cache' => true,
  //'image_resize_dimensions' => 320,
  //'image_resize_dimensions_retina' => 480,
  //'image_resize_dimensions_allowed' => '',
  //'image_resize_types' => 'jpeg, png, gif, webp, bmp',
  //'image_resize_quality' => 85,
  //'image_resize_function' => 'imagecopyresampled',
  //'image_resize_sharpen' => true,
  //'image_resize_memory_limit' => 128,
  //'image_resize_max_pixels' => 30000000,
  //'image_resize_min_ratio' => 1.5,
  //'image_resize_cache_direct' => false,
  //'folder_preview_image' => true,
  //'folder_preview_default' => '_filespreview.jpg',
  //'menu_enabled' => true,
  //'menu_show' => true,
  //'menu_max_depth' => 5,
  //'menu_sort' => 'name_asc',
  //'menu_cache_validate' => true,
  //'menu_load_all' => false,
  //'menu_recursive_symlinks' => true,
  //'layout' => 'rows',
  //'sort' => 'name_asc',
  //'sort_dirs_first' => true,
  //'sort_function' => 'locale',
  //'cache' => true,
  //'cache_key' => 0,
  //'storage_path' => '_files',
  //'files_exclude' => '',
  //'dirs_exclude' => '',
  //'allow_symlinks' => true,
  //'title' => '%name% [%count%]',
  //'history' => true,
  //'transitions' => true,
  //'click' => 'popup',
  //'click_window' => '',
  //'click_window_popup' => true,
  //'code_max_load' => 100000,
  //'topbar_sticky' => 'scroll',
  //'check_updates' => false,
  //'allow_tasks' => false,
  //'get_mime_type' => false,
  //'context_menu' => true,
  //'prevent_right_click' => false,
  //'license_key' => '',
  //'filter_live' => true,
  //'filter_props' => 'name, filetype, mime, features, title',
  //'download_dir' => 'zip',
  //'download_dir_cache' => 'dir',
  //'allow_upload' => false,
  //'allow_delete' => false,
  //'allow_rename' => false,
  //'allow_new_folder' => false,
  //'allow_new_file' => false,
  //'allow_duplicate' => false,
  //'allow_text_edit' => false,
  //'demo_mode' => false,
  //'upload_allowed_file_types' => '',
  //'upload_max_filesize' => 0,
  //'upload_exists' => 'increment',
  //'popup_video' => true,
  //'video_thumbs' => true,
  //'video_ffmpeg_path' => 'ffmpeg',
  //'video_autoplay' => true,
  //'lang_default' => 'en',
  //'lang_auto' => true,
);

## Editing config

To edit options, open the config.php file in any editor and locate the property you want to change.

```
//'root' => '',
```

Copy

Un-comment the option by removing the `//`, change the value and save:

```
'root' => '../different/path',
```

Copy

##### Can I edit configuration options directly in index.php?

You can edit config options directly in index.php, but changes will be lost if/when you upgrade Files app. Only do this if your Files app is temporary / non-persistent.

## Config options

### `root`

Assign the root path from where files and directories are loaded. With default empty `''` value, root is current directory. Path can be relative or absolute. Examples:

```
'root' => '', // default current directory, same as './''root' => 'content', // sub-directory 'content', same as './content''root' => '../', // parent directory'root' => '/var/user/eddie/', // absolute path from server root
```

Copy

### `start_path`

Assign the first directory that loads into view, by default root dir. It can be a relative or absolute path, but the dir must be inside the `root` dir.

```
'start_path' => '', // start path is same as root'start_path' => 'galleries/birds', // custom start path relative to app
```

Copy

### `username`

Add **username** and password to protect your Files app by login.

```
'username' => 'myusername',
```

Copy

### `password`

Add username and **password** to protect your Files app by login. You can encrypt your password by using our [md5() hash tool](https://www.files.gallery/tools/hash) if you don't want the password to be exposed in the PHP file.

```
'password' => 'mypassword', // non-encrypted'password' => '$2y$10$KGVfb/j9GyxQYha6bQtYEuredsqfEMs7FQEyuoEFEgIRQAdb9gQES', // encrypted
```

Copy

### `load_images`

Load preview images. If disabled, icons will display in place of images.

```
'load_images' => true, // true | false
```

Copy

### `load_files_proxy_php`

Force images and files to load via PHP proxy if they can't be accessed by URL.

```
'load_files_proxy_php' => false, // true | false
```

Copy

### `load_images_max_filesize`

Maximum image file size to load directly into galleries. If image file size exceeds this value, file icon will display instead. This option is useful to prevent massive images from loading directly into the layout, and only if you have disabled `image_resize_enabled`.

```
'load_images_max_filesize' => 1000000, // 1000000 bytes ~ 1mb
```

Copy

### `image_resize_enabled`

Allows resizing of images loaded into galleries, which is strongly recommended. Should normally be used with `image_resize_cache` enabled. _If disabled, original source images will load, which can be very slow_

```
'image_resize_enabled' => true, // true | false
```

Copy

### `image_resize_cache`

Allow caching of resized images to drastically improve loading speed on consecutive visits. Resized images will normally get cached in your `storage_path` at `_files/cache/images/*`.

```
'image_resize_cache' => true, // true | false
```

Copy

### `image_resize_dimensions`

Default resized image dimensions. Default 320 is a good balance between visible quality and file size.

```
'image_resize_dimensions' => 320,
```

Copy

### `image_resize_dimensions_retina`

Resize image dimensions for high-density (retina) screens. This allows you to serve higher quality images for HiDPI screens, at the cost of slightly larger file size and more cache files in storage. Set this option to 0 if you want to disable it.

```
'image_resize_dimensions_retina' => 480,
```

Copy

### `image_resize_dimensions_allowed`

Comma-separated list of allowed resize dimensions, in addition to the two defaults. Not used directly in Files app, but useful if you want to configure additional image sizes for other apps that use Files, like Embed app. For example '640, 800, 1024'.

```
'image_resize_dimensions_allowed' => '', // empty, only image_resize_dimensions and image_resize_dimensions allowed'image_resize_dimensions_allowed' => '640, 800, 1024', // additional resize dimensions [640, 800, 1024] allowed
```

Copy

### `image_resize_types`

Commma-separated list of image types to resize. Useful for example if you want to exclude PNG/GIF images to retain transparency and animations.

```
'image_resize_types' => 'jpeg, png, gif, webp, bmp',
```

Copy

### `image_resize_quality`

JPG compression level for resized images.

```
'image_resize_quality' => 85,
```

Copy

### `image_resize_function`

Choose between [imagecopyresampled](http://www.php.net/imagecopyresampled) (smoother) and [imagecopyresized](http://www.php.net/imagecopyresized) (faster). Difference is minimal, but you could use imagecopyresized for example if you want faster resizing when not using image resize cache.

```
'image_resize_function' => 'imagecopyresampled',
```

Copy

### `image_resize_sharpen`

Creates sharper (less blurry) preview images.

```
'image_resize_sharpen' => true,
```

Copy

### `image_resize_memory_limit`

Temporarily increases PHP memory limit (if required) when resizing large images. Default value is set to 128 MB, which allows resizing images up to ~ 6000 px. If your default PHP `memory_limit` is already higher than the assigned value, it will have no effect.

```
'image_resize_memory_limit' => 128, // number
```

Copy

### `image_resize_max_pixels`

Sets the maximum allowed pixels (dimensions) when resizing images. Default value is 30000000 (30 megapixels), which allows resizing images up to approximately 6000 x 5000 px. This option is in place to protect server from attempting to resize image sizes beyond capabilities and/or to prevent slow performance.

```
'image_resize_max_pixels' => 30000000, // number
```

Copy

### `image_resize_min_ratio`

Minimum ratio difference between image resize target dimensions and source image dimensions. If the source image is only X times larger than the resize target, the source image will be used. It's pointless to create resized images if the source is only slightly larger than the resize target.

```
'image_resize_min_ratio' => 1.5, // number
```

Copy

### `image_resize_cache_direct`

Will attempt to load direct path of cached resized images into the gallery, bypassing PHP proxy. May cause faster image loading and browser caching. However, if this option is enabled and you delete image cache, you may end up with missing image files because you are bypassing the PHP proxy that checks if cached resized images exist. If this option is enabled and you delete the image cache, you may need to increase `cache_key`.

```
'image_resize_cache_direct' => false,
```

Copy

### `folder_preview_image`

Attempts to load preview images for all folders. This could be slow on large folders and/or slow server.

```
'folder_preview_image' => true,
```

Copy

### `folder_preview_default`

Always prioritize this filename as folder preview image if it exists in folder. Useful if you want to assign a specific image for some folders, or if you want to assign hidden preview images or if you simply want to avoid the performance hit of scanning each dir for first image to use as preview.

```
'folder_preview_default' => '_filespreview.jpg',
```

Copy

### `menu_enabled`

Toggle the left folder menu on or off. You can still navigate folders from within the main view area. _\* If the root dir doesn't contain any folders, the menu will always be disabled._

```
'menu_enabled' => true,
```

Copy

### `menu_show`

Toggle the left folder menu expanded or collapsed by default. This option has no effect on small screens (mobile), where the menu is always collapsed by default. The value is remembered by the browser on toggle and will always default to the last state the menu was in.

```
'menu_show' => true,
```

Copy

### `menu_max_depth`

Assign the maximum depth of recursive folders to load into the left menu. This is a precaution to prevent loading unlimited levels of folders into the menu, which may be slow and unproductive for large directory structures. Users can still navigate to deeper folder levels directly from the view area.

```
'menu_max_depth' => 5,
```

Copy

### `menu_sort`

Decides how the left folders menu is sorted, with options `name_asc`, `name_desc`, `date_asc` and `date_desc`.

```
'menu_sort' => 'name_asc', // name_asc, name_desc, date_asc, date_desc
```

Copy

### `menu_cache_validate`

When enabled, menu cache will be validated to make sure it matches the actual folder structure. This mechanism is normally necessary to make sure any changes you make (new folders etc) are validated vs the menu cache file. If disabled, menu will load faster, but the cache is only validated against root and root child-folders. This feature may be useful if you have a heavy but persistent (non-changing) folder structure, and want the menu to load fast. IF enabled and you make changes in subfolders (new folder), you will need to either delete the menu cache `_files/cache/menu/*` or increase option `cache_key`.

```
'menu_cache_validate' => true,
```

Copy

### `menu_load_all`

When enabled, all folders in the menu will preload. When clicking items in the menu, pages will then display instantaneously without loading. This feature is useful for persistent galleries and/or simple root folder structures.

```
'menu_load_all' => false,
```

Copy

### `menu_recursive_symlinks`

List sub-directories of symlinks in the main menu. May cause harmless menu loops or duplicate items in the menu.

```
'menu_recursive_symlinks' => true,
```

Copy

### `layout`

Default gallery layout from options list, imagelist, blocks, grid, rows or columns. Layout is additionally controlled from the topbar layout dropdown menu, in which case it will override default layout.

```
'layout' => 'rows', // list, imagelist, blocks, grid, rows, columns
```

Copy

### `sort`

Default sorting for files from options name, date, filesize and kind (file type), in ascending or descending order. Sorting is additionally controlled from the topbar sort dropdown menu, in which case it will override default sort.

```
'sort' => 'name_asc', // name_asc, name_desc, date_asc, date_desc, filesize_asc, filesize_desc, kind_asc, kind_desc
```

Copy

### `sort_dirs_first`

When enabled, folders will always display first when mixed with files.

```
'sort_dirs_first' => true,
```

Copy

### `sort_function`

Assigns the sort function used for sorting file names. With default `locale` option, sorting is handled by Javascript [localeCompare()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare), which sorts cAsE-insensitive, numbered names \[2name<10name\] and resolves unicode \[èáø\] depending on browser locale. Optionally, `basic` sort is slightly faster, but may not resolve numbered names and unicode correctly. You can also specify a [locale](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare#syntax), which decides the language to be used for `localeCompare()` sorting.

```
'sort_function' => 'locale', // 'locale', 'basic', '[locale]'
```

Copy

### `cache`

When enabled, JSON cache files will be created for menu and folders. This is strongly recommended, as it allows the menu and folders to load much faster after first visit. The cache is normally created in `_files/cache/*`. You can disable this option if you don't want Files app to create and cache files.

```
'cache' => true,
```

Copy

### `cache_key`

Cache data is validated vs a cache\_key. Although cache will normally update automatically, if you want to force the cache to refresh, you can increase the cache\_key number.

```
'cache_key' => 0,
```

Copy

### `storage_path`

Defines where Files app will store cache, config and other application data. Set to `_files` by default, which means all data will be stored inside folder `_files/*` relative to the application. You won't normally need to change this value, unless you want to store data in a different location, or if you have multiple Files applications that share the same storage. Storage path can be absolute or relative to the app.

```
'storage_path' => '_files',
```

Copy

### `files_exclude`

PHP regex normally used to exclude or include only certain file types and folders. The regex is applied on the file name (basename) without the path. You can test regular expressions at [phpliveregex.com](https://www.phpliveregex.com/).

```
'files_exclude' => '', // empty default, no files are excluded'files_exclude' => '/\.(pdf|jpe?g)$/i', // excludes all files that end with .pdf, .jpeg and .jpg / case insensitive
```

Copy

### `dirs_exclude`

A PHP regex to exclude certain paths and folders. The regex is applied on the folder path relative to root.

```
'dirs_exclude' => '', // empty default, no folders are excluded'dirs_exclude' => '/\/eleph|\/football(\/|$)/i', // exclude dirs that start with "eleph" and dirs that match /football/*
```

Copy

### `allow_symlinks`

Allows Files app to display and follow symlinks. Mostly works fine, but you may face issues if you have symlinks that point to locations on disk with different permissions or to locations that are not within the website document root.

```
'allow_symlinks' => true,
```

Copy

### `title`

Assign custom page `<title>`. You can include variables `%name%`, `%path%` and `%count%`. If you need advanced behavior, you can use `_c.config.title` function in [advanced javascript](https://www.files.gallery/docs/javascript-config/) instead.

```
'title' => '%name% [%count%]',// 'title' => 'My website name › %name% [%count%]', // example with custom string prepended
```

Copy

### `history`

When enabled, browser will change URL ?path/to/folder as you navigate folders. This also allows deep-linking directly to files and folders when sharing an URL.

```
'history' => true,
```

Copy

### `transitions`

Enables transitions when navigating between pages.

```
'transitions' => true,
```

Copy

### `click`

Choose what method to trigger when clicking items in the list. Default value "popup" will apply for all image/video files, falling back to "modal" for non-image files.

```
'click' => 'popup', // popup, modal, download, window or menu
```

Copy

### `click_window`

Comma-separated list of file extensions that you want to open directly in new window on click. Useful for easy viewing of PDF, HTML and text files, instead of opening a preview in Files app first.

```
'click' => '', // empty, all file types open in click default'click' => 'pdf, html', // Opens PDF and html in new browser window, allowing them to be previewed
```

Copy

### `click_window_popup`

Opens browser windows from `click_window` in a popup-style browser window, overlaying current window. Useful when previewing PDF, html and text-type documents. _\* Does not apply for mobile devices, where new window will open as normal._

```
'click_window_popup' => true,
```

Copy

### `code_max_load`

Maximum file size for text/code files to load and preview in the code viewer/editor. The purpose of this is to prevent massive text files from causing a sluggish interface in the code syntax highlighter.

```
'click_window_popup' => 100000, // default 100000 ~ 100kb
```

Copy

### `topbar_sticky`

Choose how the topbar attaches itself to screen. Default value `scroll` will attach the topbar to top of screen on scroll up, `true` will cause the topbar to always remain fixed, while `false` will disable fixed topbar and revert to normal behavior.

```
'topbar_sticky' => 'scroll', // 'scroll', true, false
```

Copy

### `check_updates`

Checks for Files app updates and displays a bell icon in topbar if there is an update available, allowing user to "update", "download" or "read more".

```
'check_updates' => false,
```

Copy

### `allow_tasks`

Tasks plugin to manage cache. _\* Not yet documented._

```
'allow_tasks' => null,
```

Copy

### `get_mime_type`

Set to true to detect file mime type from server/PHP (slow) instead of from file extension (faster). This should not be necessary, unless you have file types with incorrect file extensions or if you want to validate file types on server for security reasons.

```
'get_mime_type' => false,
```

Copy

### `context_menu`

Enables context-menu button and right-click menu with options.

```
'context_menu' => true,
```

Copy

### `prevent_right_click`[](https://www.files.gallery/docs/config//#prevent_right_click "Direct link to heading")

Enable to block browser right-click menu on sensitive items (images, list items, menu).

```
'prevent_right_click' => false,
```

Copy

### `license_key`

Insert license key here to unlock features and remove license popup.

```
'license_key' => 'XX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX',
```

Copy

### `filter_live`[

Live search filtering on keyboard input. If disabled, input filter requires keyboard-return or unfocus to trigger, which may be useful if you have 1000's of files in folders and want to prevent slow filtering from triggering unnecessarily _\* Does not apply for mobile devices, which allways triggers on "search" or keyboard-hide._

```
'filter_live' => true,
```

Copy

### `filter_props`

File properties to use when filtering, more properties will cause slower processing. Properties name, filetype and mime apply for all file types, while features, title, headline, description, creator, credit, copyright, keywords, city, sub-location and province-state are available to image files with IPTC meta.

```
'filter_props' => 'name, filetype, mime, features, title', // default'filter_props' => 'name, filetype, mime, features, title, headline, description, creator, credit, copyright, keywords, city, sub-location, province-state', // all
```

Copy

### `download_dir`

Set to `zip` to add an option to download all files in folder as a zip file. This option requires [PHP ZipArchive](https://www.php.net/manual/en/class.ziparchive.php), and requires the server to first compress all files into the zip before serving it (which could be slow, until it gets cached with `download_dir_cache`). Optionally, set to `files` for multi-file download directly in browser, which works nicely on desktop without having to zip files on server first, but does not work on mobile devices.

```
'download_dir' => 'zip', // 'zip', 'files', '' (disabled)
```

Copy

### `download_dir_cache`

Enables caching of created zip files when `download_dir` option is set to `zip`. This is recommended for performance, so that zip files don't need to get created every time any visitor clicks to download. Set to `dir` to store the `_files.zip` directly in the current folder or set to `storage` to store inside `_files/zip/*`. Default `dir` option is most effective, because it allows files app to check if the zip-cache is valid and updated, even if you change folder name.

```
'download_dir_cache' => 'dir', // 'dir' / 'storage' / '' /
```

Copy

### `allow_upload`

Allow uploading files.

```
'allow_upload' => false, // true | false
```

Copy

### `allow_delete`

Allow deleting files.

```
'allow_delete' => false, // true | false
```

Copy

### `allow_rename`

Allow renaming files.

```
'allow_rename' => false, // true | false
```

Copy

### `allow_new_folder`

Allow creating new folders.

```
'allow_new_folder' => false, // true | false
```

Copy

### `allow_new_file`

Allow creating new files.

```
'allow_new_file' => false, // true | false
```

Copy

### `allow_duplicate`

Allow duplicating files.

```
'allow_duplicate' => false, // true | false
```

Copy

### `allow_text_edit`

Allow editing text and code files.

```
'allow_text_edit' => false, // true | false
```

Copy

### `demo_mode`

When enabled, all filemanager operations will be blocked. Mainly used for the Files app demo.

```
'demo_mode' => false, // true | false
```

Copy

### `upload_allowed_file_types`

Comma-separated list of allowed upload file types. List may contain extensions or mime-types with partial match, for example `pdf, doc, image/*`. When empty (default), all file types are allowed.

```
'upload_allowed_file_types' => '', // default, all file types are allowed'upload_allowed_file_types' => 'pdf, doc, image/*', // *.pdf, *.doc and all image types are allowed
```

Copy

### `upload_max_filesize`

Sets the maximum file size (bytes) allowed for uploads. Default value 0 means no limit, but maximum file size will always be limited by your server's PHP `upload_max_filesize` value.

```
'upload_max_filesize' => 0, // default, no limit'upload_max_filesize' => 1000000, // maximum file size 1000000 ~ 1MB
```

Copy

### `upload_exists`

Decides what to do if uploaded filename already exists in upload target folder. Default 'increment' will rename uploaded files by appending a number, 'overwrite' will overwrite existing files while 'fail' will cause the upload to fail.

```
'upload_exists' => 'increment', // increment filename, for example filename.jpg => filename-2.jpg'upload_exists' => 'overwrite', // overwrite existing file if filename exists'upload_exists' => 'fail', // upload fail of filename exists
```

Copy

### `popup_video`

When enabled, opens video formats in the popup, allowing user to navigate between other popup items. If disabled, video will open in simple modal.

```
'popup_video' => true,
```

Copy

### `video_thumbs`

Create thumbnails for video files. This option requires [FFmpeg](https://ffmpeg.org/) and PHP [exec()](https://www.php.net/manual/en/function.exec.php) enabled. Processing video thumbnails is slow, but they will get cached just like resized images

```
'video_thumbs' => true, // true | false
```

Copy

### `video_ffmpeg_path`

Path to [FFmpeg](https://ffmpeg.org/) command-line for video thumbnail creation. Normally just 'ffmpeg', but some servers require a full path to the [FFmpeg](https://ffmpeg.org/) application.

```
'video_ffmpeg_path' => 'ffmpeg',
```

Copy

### `video_autoplay`

Autoplay videos when user clicks to open them in popup.

```
'video_autoplay' => true,
```

Copy

### `lang_default`

Default interface language if browser language is not supported or `lang_auto` is disabled.

```
'lang_default' => 'en',
```

Copy

### `lang_auto`

Automatically assign interface language based on detected browser language.

```
'lang_auto' => true,
```
