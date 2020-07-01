

![NovemberGallery Banner](https://novembergallery.zenware.io/storage/app/media/november-gallery-octobercms-banner.jpg)

<div align="right"><a href="https://gitter.im/november-gallery/community?utm_source=badge&amp;utm_medium=badge&amp;utm_campaign=pr-badge&amp;utm_content=badge"><img src="https://badges.gitter.im/november-gallery/community.svg" alt="Join the chat at https://gitter.im/november-gallery/community"></a></div>

Check out the [live demo site](https://novembergallery.zenware.io)!

A gallery plugin for professional Photographers, Media Artists, Bloggers and Content Publishers.

 1. Upload your images either using the Media Manager built into OctoberCMS or through the dedicated galleries backend page
 3. Drop November Gallery onto your page or partial* or static page
 4. Select the folder you uploaded your images to and how you want them displayed using the component inspector, or in your RainLab blog entry

<small><i>*please read the Known Issues section regarding usage in partials!</i></small>

Behind the scenes, November Gallery makes use of the [Image Resizer plugin](https://octobercms.com/plugin/toughdeveloper-imageresizer) to generate thumbnails of your images, and the excellent [UniteGallery jQuery Gallery Plugin](https://github.com/vvvmax/unitegallery) as well as [Swiper](https://idangero.us/swiper/). 

This README is an abridged version of the full documentation that we call [The November Gallery Cookbook](https://its.zensoft.hu/books/november-gallery-cookbook).

# Features:

- Works in Pages, Partials, "Static" Pages, and Blog Posts!
- Five components included: 
	 - **Embedded Gallery** if you wish to show a gallery of images or thumbnails in your page, arranged in various layouts: **tiles** (arranged in columns, justified, or laid out in a grid "masonry style"), **carousel**, **slider**, or **combined** (large image + lightbox)
	 - **Swiper Gallery** for responsive, multi-platform galleries
	 - **Popup Lightbox** for galleries that can be opened from a link or button on your page, with several available styles (wide, compact)
	 - **Video Gallery** for...videos, again, with several "styles" available (thumbs / titles + subtitles / titles only)
	 - **Image List Only** if you want to handle the display of the images yourself and only need a list of image objects
 - Set which folder of images to display in the component configuration panel OR pass it dynamically as a page-variable OR set it in your RainLab blog entry
 - Responsive/touch enabled/skinnable/themable/gallery buttons/keyboard control etc.

### Limitations / ToDo:
 
 - [ ] Improve handling of videos uploaded to the site
 - [ ] Expand docs with example for "dynamic" gallery via path variables
 - [ ] Add alternative lightbox/carousel gallery script support
 - [ ] Support titles & captions embedded into the image files, or in sidecar files (with support for multiple languages) (titles & captions are only supported when uploading through the backend "Gallery" page)
 - [ ] Cache image data in database instead of reading it all in from the filesystem every time

# Deployment & Installation

For more information see the [OctoberCMS docs](https://octobercms.com/docs/cms/pages#injecting-assets)!

# Usage

For further usage examples and documentation please see [The NovemberGallery Cookbook](https://its.zensoft.hu/books/november-gallery-cookbook)


### (1) Prepare and Upload your Images

You can choose to upload your images either using the "Gallery" page in the October back-end, or you can use the built-in Media Manager. 

> Hint: The dedicated back-end November Gallery management page gives you more options for giving your images titles and subtitles, and you can also arrange the order easily; on the other hand, if you ever end up deleting the plugin, October will also delete all of your albums created there. Use the October built-in Media Manager to upload your images if you don't need the extra features provided by the November Gallery management page. Going the Media Manager route also allows you to upload hundreds of images using an FTP client or other file manager; this is not possible through the Gallery page.

<details>
<summary>Read more...</summary>

Although the plugin will automatically generate thumbnails of your pictures, the full-size images will be displayed as-is. Therefore, it's a good idea to resize all of your pictures before uploading them to the gallery. A plethora of free options exist to help you with that, we ♥ [FastStone Image Viewer](https://www.faststone.org) (Windows), [Fast Image Resizer](https://adionsoft.net/) (Windows), and [Image Resizer for Windows](http://www.bricelam.net/ImageResizer/). There are great options out there for Mac as well. A typical screen resolution nowadays is around 1920 x 1680 pixels - so if you're looking to allow your users to see your pictures in top quality full-screen, then resize them to fit within these constraints.

Also, make sure that your photos are in a format that web browsers understand, such as .jpg or .png, or .gif (the latter is more suitable for graphics with fewer colors and geometric lines, such as charts or icons).

Finally, upload your pictures using the "Gallery" admin area, or through the October Media manager into the folders you created earlier.

#### Uploading through the back-end Gallery management page

This is fairly self-explanatory. Log into your site back-end and find the "Gallery" button at the top. Create an album, and upload your pictures!

#### Uploading through the Media Manager

Images must be organized into folders. Although you can use any folder structure that you'd like, we recommend that you create a "root" folder and create separate folders underneath it to store your albums. You can optionally create separate "root" folders to store your images, videos, and blog pictures. Avoid using spaces or special characters in your folder names. Your folder structure may look like this:

- my_galleries
	- my_travels
		- 2018-argentina
		- 2015-vietnam
		- 2010-hungary
	- cat_pictures
	- awesome_vacuum_cleaners

#### Uploading using FTP

This is the most robust way for uploading many pictures at once to your site. Use an FTP client such as [FileZilla](https://filezilla-project.org/) (Windows) or [WinSCP](https://winscp.net/)  (Windows) or [Panic Transmit 5](https://panic.com/transmit/) (Mac) and connect to your server. Your media files will be located in `public_html/storage/app/media`. You can create new folders through FTP as well, and if you then use the back-end media manager, you'll see them. 
</details>

### (2) Configure The Plugin
Log into your "backend" and go to Settings → November Gallery to configure your defaults. Things to look out for:

 - `Settings` Tab: Select the folder that you created your galleries under from the Base Media Folder drop-down, you can also select a default layout for your galleries. 
- `Thumbnails` Tab: It is recommended to use the image resizer to automatically generate thumbnails of your pictures. For this, make sure that the "Use Image Resizer" option is ON on the Thumbnails plugin configuration tab. You can also set either the width or the height for your thumbnails here.
- `Advanced` Tab: *Inject UniteGallery Assets* should probably be on. If your theme already includes jQuery, then you can set *Inject jQuery* to OFF.

### (3) Drop the Plugin Onto your CMS Page(s)

The plugin provides four components that you can drop onto your CMS Pages/Partials*/Layouts, it also works as a "Snippet" in static pages.

<small><i>*please read the Known Issues section regarding usage in partials!</i></small>

### [Shared Options]

Property | Inspector Name | Description
--|--|--
`alias`|Alias|Standard OctoberCMS stuff, you refer to the component in  your page via this unique identifier, the default is "embeddedGallery" but you can change it to anything you want (don't use spaces or special characters though!)
`mediaFolder`|Media Folder|Select the folder that you uploaded the images to in the OctoberCMS Media manager. Only folders under the "Base Media Folder" set on the November Gallery settings page are valid.
`maxItems`|Max Images|The maximum number of images to display
`sortBy`|Order by|Order to display the gallery items in; note: Image Title, Description, and Sort Order only work for images uploaded using the Galleries page! Options are: <br><small>-  `title` / Image Title<br>- `description` / Image Description<br>- `sortOrder` / Image Order in Gallery<br>- `width` / Image Width<br>- `height` / Image Height<br>- `orientation` / Image Orientation<br>- `fileName` / Filename<br>- `fileSize` / File Size <br>- `uploaded` / Date/Time Uploaded;</small> <br>and all options are also available in reverse order (append DESC onto the option code).
<br>
<br>

## Component 1: Embedded Gallery

Use this if you wish to show a gallery of images within your page using various layouts, with optional full-screen (lightbox-style) viewing.

### [Options]
The following are available in addition to the [Shared Options](#shared-options) described above:

Property | Inspector Name | Description
-- | -- | --
`galleryLayout` | Gallery Layout | Select a gallery layout; possible values are:<br><small>- `default` / Default (use the gallery layout set on the plugin settings page)<br>- `gallery_tiles` / Tiles<br>- `gallery_carousel` / Carousel<br>- `gallery_combined` / Combined<br>- `gallery_slider` / Slider<br>Check out <a href="https://novembergallery.zenware.io/demo/embedded-gallery-tiles" target="_blank">the demo site</a> for live examples of each layout.</small>
`tilesLayout` | Tile Layout | Only applicable if the *Gallery Layout* is set to "Tiles"; possible values are:<br><small>- `default` / Default (use the default gallery layout set on the plugin settings page)<br>- `gallery_tiles_columns` / Columns<br>- `gallery_tiles_justified` / Justified<br>- `gallery_tiles_nested` /  Nested<br>- `gallery_tiles_grid` / Grid</small>
`combinedLayout` | Thumbnails Layout | Only applicable if the *Gallery Layout* is set to "Combined"; possible values are:<br><small>- `default` / Default (use the default thumbnails layout set on the plugin settings page)<br>- `gallery_combined_default` / Normal (default)<br>- `gallery_combined_compact` / Compact<br>- `gallery_combined_grid` /  Grid</small>
`additionalGalleryOptions` | Script options | Additional JS options that you want passed onto the UniteGallery script, for example: `theme_panel_position: "bottom"`
`imageResizerWidth` | Thumbnail Width | Width of the generated thumbnail; Leave empty or set to 0 to only constrain the image by height; leave both width and height empty to fall back on the values set on the backend plugin configuration page
`imageResizerHeight` | Thumbnail Height | Height of the generated thumbnail; Leave empty or set to 0 to only constrain the image by height; leave both width and height empty to fall back on the values set on the backend plugin configuration page
`imageResizerMode` | Thumbnail Mode | Select how to resize your images into thumbnails, or select "default" to use the thumbnail mode set on the plugin settings page; possible values are: <small><br>- Default<br>- Exact<br>- Portrait<br>- Landscape<br>- Auto<br>- Crop</small>
`galleryWidth` | Gallery Width | Can be a number (pixel lenght) or a percent (of the parent container). Leave empty to fall back on the values set on the backend plugin configuration page
`galleryHeight` | Gallery Height| Only applies to "Combined" and "Slider" galleries! Can be a number (pixel lenght) or a percent (of the parent container). Leave empty to fall back on the values set on the backend plugin configuration page

For an explanation of page propreties, see [Component: Image List Only](#component-image-list-only). For a more in-depth explanation as well as examples, see [The NovemberGallery Cookbook](https://its.zensoft.hu/books/november-gallery-cookbook)

### [Customizing the Gallery]

You have several options to customize how your gallery looks and behaves, depending on how deep you are willing to go down the rabbit hole:

 1. You can customize the gallery to some extent through the inspector; for example, you can set the gallery layout
 2. You can also add some CSS to control how the thumbnails are displayed
 3. You can add some custom options that will be passed onto the UniteGallery script via the inspector
 4. You can override the component partial

<details>
<summary>Read more...</summary>

**Example 1: Set the thumbnail size for all galleries**

You can set the thumbnail size on the plugin backend settings page: **Settings → November Gallery → Thumbnails**. If you want more control, go to **Settings → Image Resizer Settings**

**Example 2: Set the thumbnail size for an individual gallery**

You can set the thumbnail size for a specific gallery on the component properties page (a.k.a. "Inspector").

**Example 3: Set the gallery dimensions for the "combined" gallery**

In the combined gallery, a large image is displayed along with a row of thumbnails. First, set your thumbnail size using the inspector let's say to 100. 
Then check the [relevant options available](http://unitegallery.net/index.php?page=default-options) for the combined gallery on the UniteGallery plugin page. You can see that the "gallery_width" and "gallery_height" options control the overall size of the gallery. So enter something like the following into the *Script options* component option: `gallery_width:900,gallery_height:700,thumb_fixed_size:false`

The thumbnail size you defined using the inspector will control the size of the generated thumbnails, it will also automatically add a "thumb_height" option to the gallery. You can override this if you wish by manually adding a "thumb_height" option under *Script options*, but this should not be necessary. The `thumb_fixed_size:false` setting enables dynamically sized thumbnails.

**Example 4: Set the spacing between tiled images**

First, review [what options you have for the various tiled galleries](http://unitegallery.net/index.php?page=tiles-columns-options) on the UniteGallery website. You can see that for the Tiles - Columns layout,  you can control the spacing between the columns with the `tiles_space_between_cols:  3` option -- so add it to the *Script options* NovemberGallery component option!

**Example 5: Override the component partial**

It is easy to override the default partial by following the [OctoberCMS documentation](https://octobercms.com/docs/cms/components#overriding-partials). All you have to do is go to your `Partials` and create a folder with the same name as the alias of your gallery. Create a "default.htm" file in that directory and copy the contents of the default component partial for the given gallery type into this folder. 

Gallery Type | Default Component Partial Path
-- | --
Embedded Gallery | [/plugins/zenware/novembergallery/components/embeddedgallery/default.htm](https://github.com/lieszkol/november-gallery/blob/master/components/embeddedgallery/default.htm)
Swiper | [/plugins/zenware/novembergallery/components/swipergallery/default.htm](https://github.com/lieszkol/november-gallery/blob/master/components/swipergallery/default.htm)
Pop-up Lightbox | [/plugins/zenware/novembergallery/components/popupgallery/default.htm](https://github.com/lieszkol/november-gallery/blob/master/components/popupgallery/default.htm)
Video Gallery | [/plugins/zenware/novembergallery/components/videogallery/default.htm](https://github.com/lieszkol/november-gallery/blob/master/components/videogallery/default.htm)
Image List Only | [/plugins/zenware/novembergallery/components/customgallery/default.htm](https://github.com/lieszkol/november-gallery/blob/master/components/customgallery/default.htm)

</details>
<br>
<br>

## Component 2: Swiper

Use this component to create a modern, responsive "swiper" that can be controlled easily from any device. Note that you can control any of the galleries by touch (or click-and-swipe using a mouse). Various transitions are available: "fade", "slide", "flip", "cube", etc..

### [Options]
The following are available in addition to the [Shared Options](#shared-options) described above:

Property | Inspector Name | Description
-- | -- | --
`effect` | Transition Effect | Tranisition effect. Can be "slide", "fade", "cube", "coverflow" or "flip"
`direction` | Direction | Can be "horizontal" or "vertical"
`speed` | Transition Speed | How long the transition effect lasts, in milliseconds. 1000 = 1 seconds.
`lazyLoad` | Lazy-load images? | Toggle ON to only load the images the user is looking at. Previous and next images are set to pre-load automatically.
`addPagination` | Add pagination? | Toggle ON to show bullets (or anything else) that enable to user to jump to any specific slide.
`addNavigation` | Add navigation? | Toggle ON to show previous-slide and next-slide navigational arrows.
`autoplay` | Auto-play? | Toggle ON to enable automatic advance on the slides. Set the delay below.
`autoplayDelay` | Auto-play Delay | How long each image is shown for, in milliseconds. 1000 = 1 seconds.
`additionalGalleryOptions` | Script options | Additional JS options that you want passed onto the Swiper script, for example: `fadeEffect: {crossFade: true}`
`useDescriptionAsCSS` | Description is Style | Inject the image description as CSS for that image; only works for images uploaded through the backend Gallery page.
`mediaQuery` | Media Query | You can set a media query to only apply the style in certain circumstances. Do not include a trailing "{". For example: <br><small><code>@media screen and (max-width: 766px) and (orientation: portrait)</code></small>


**Example Page**
```html
<div style="width: 100%; height: calc(100vh - 70px);">
	{% component 'swiperGallery' %}
</div>
```

The swiper component by default fills whatever space it is in, in this case we set the container DIV to take up 100% of the viewport and be 100vh tall.

For examples on how to customize the gallery, see [Customize the Gallery](#customizing-the-gallery) above.
<br>
<br>

## Component 3: Pop-up Lightbox

Use this if you wish to add a lightbox-style 'pop-up' gallery to your page that is only shown when the user clicks on an element (such as a link/button/image).

### [Options]
The following are available in addition to the [Shared Options](#shared-options) described above:

Property | Inspector Name | Description
-- | -- | --
`attachTo` | Attach to | JQuery selector for the element(s) that the user can click on to open the lightbox; for example: `#gallery-button`
`additionalLightboxOptions` | Script options | Additional JS options that you want passed onto the UniteGallery script, for example: `theme_panel_position: "bottom"`


**Example Page**
```html
{% component 'popupLightbox' %}
<button id="gallery-button">Click me!</button>
```

This is a simple example where you place a button onto the page. Select a folder of images from the "Media Folder" drop-down in your inspector, and set the gallery "Attach to" option to `#gallery-button`. Your button should then serve to open a lightbox gallery of all of the images in the selected folder.

For examples on how to customize the gallery, see [Customize the Gallery](#customizing-the-gallery) above.
<br>
<br>

## Component 4: Video Gallery

Use this gallery to display videos inline. You can choose to upload your videos to your website or to show videos hosted on YouTube/Vimeo/Wistia.

### [Options]
The following are available in addition to the [Shared Options](#shared-options) described above:

Property | Inspector Name | Description
-- | -- | --
`videoGalleryItemsSelector` | Gallery Selector/ID | JQuery selector for the element that holds the video items; for example: `#videos`
`videoGalleryLayout` | Gallery Layout | Select a gallery layout; possible values are:<br><small>- `default` / Default (use the gallery layout set on the plugin settings page)<br>- `video_gallery_right_thumb` / Thumbnails <br>- `video_gallery_right_title_only` / Titles Only<br>- `video_gallery_right_no_thumb` / No Thumbnails<br>Check out <a href="https://novembergallery.zenware.io/demo/video-gallery" target="_blank">the demo site</a> for live examples of each layout.</small>
`additionalVideoGalleryOptions` | Script Options | Additional JS options that you want passed onto the UniteGallery script, for example: `theme_autoplay: true`
`imageResizerHeight` | Thumbnail Height | Height of the generated thumbnail; Leave empty or set to 0 to only constrain the image by height; leave both width and height empty to fall back on the values set on the backend plugin configuration page
`imageResizerMode` | Thumbnail Mode | Select how to resize your images into thumbnails, or select "default" to use the thumbnail mode set on the plugin settings page; possible values are: <small><br>- Default<br>- Exact<br>- Portrait<br>- Landscape<br>- Auto<br>- Crop</small>
`galleryWidth` | Gallery Width | Can be a number (pixel lenght) or a percent (of the parent container). Leave empty to fall back on the values set on the backend plugin configuration page
`galleryHeight` | Gallery Height| Only applies to "Combined" and "Slider" galleries! Can be a number (pixel lenght) or a percent (of the parent container). Leave empty to fall back on the values set on the backend plugin configuration page

For examples on how to customize the gallery, see [Customize the Gallery](#customizing-the-gallery) above.
<br>
<br>

## Component 5: Image List Only

Use this if you wish to write your own Twig script for displaying your images, and only need a list of images (that can be found in a given folder) to be loaded into a page variable. 

The image list component does not have any options other than the [Shared Options](#shared-options) described above.

**Example Page 1**
```html
<div style="display: flex; flex-wrap: wrap; justify-content: center; align-items: center;">
{% for galleryitem in customGallery.gallery.items %}
    <div>
        <a href="{{ galleryitem.url }}" target="_blank">
            <img src="{{ galleryitem.url | resize(280, false,  { mode: 'portrait', quality: '90', extension: 'png' }) }}" alt="{{ galleryitem.fileName }}" style="margin: 20px;" />
        </a>
    </div>
{% endfor %}
</div>
```
This example assumes that your gallery component has the alias "customGallery" and that you have the [Image Resizer](https://octobercms.com/plugin/toughdeveloper-imageresizer) plugin installed. Thumbnails are generated for the images and displayed in a flexbox, with each thumbnail providing a link to the full-resolution image.

**Example Page 2**
```html
<div class="container-fluid">
{% for galleryitemchunk in customGallery.gallery.items.sortBy('fileName').chunk(3) %}
    <div class="row">
        {% for galleryitem in galleryitemchunk %}
            <div class="col-xs-4" style="text-align: center;">
                <a href="{{ galleryitem.url }}" target="_blank">
                    <img src="{{ galleryitem.url | resize(280, false,  { mode: 'portrait', quality: '90', extension: 'png' }) }}" alt="{{ galleryitem.fileName }}" />
                </a>
            </div>
        {% endfor %}
    </div>
{% endfor %}
</div>
```
Again, we are assuming that your component has the alias "customGallery" and that you have the [Image Resizer](https://octobercms.com/plugin/toughdeveloper-imageresizer) plugin installed. The images are [sorted](https://octobercms.com/docs/services/collections#method-sortby) by filename and "[chunked](https://octobercms.com/docs/services/collections#method-chunk)" into groups of 3 images, which are then displayed using the [Bootstrap grid layout](https://getbootstrap.com/docs/4.0/layout/grid/).

Check out the [Demo Site](https://novembergallery.zenware.io/demo/image-list-only) for live examples of the above.

### Page Properties

**`__SELF__.gallery`**<br>
Type: [ZenWare\NovemberGallery\Classes\Gallery](https://github.com/lieszkol/november-gallery/blob/master/classes/Gallery.php)<br>
Gallery class, holds the various properties of the gallery instance.

#### Gallery Properties

Property | Type | Description
--|--|--
`items` | [October\Rain\Support\Collection](https://octobercms.com/docs/services/collections) | Collection of gallery items, see below.
`orderBy` | string | The GalleryItem property by which the gallery should be sorted (as set in the component inspector)


**`__SELF__.gallery.items`**<br>
Type: [October\Rain\Support\Collection](https://octobercms.com/docs/services/collections)<br>
also see [API Docs](https://octobercms.com/docs/api/october/rain/database/collection),  [Illuminate\Database\Eloquent\Collection](https://laravel.com/api/5.5/Illuminate/Database/Eloquent/Collection.html) and [Illuminate\Support\Collection](https://laravel.com/api/5.5/Illuminate/Support/Collection.html)

Collection of `ZenWare\NovemberGallery\Classes\GalleryItem` classes. Serving it as a collection gives access to a ton functionality that is not available with a simple array. For example, you could choose to sort the images by filename:
```html
{% for galleryitem in customGallery.gallery.items.sortBy('fileName') %}
   <img src="{{ galleryitem.url }}" />
{% endfor %}
```
<details>
<summary>Read more...</summary>

#### GalleryItem Properties

Property | Type | Description
--|--|--
`title` | string | Image title metadata, available for images uploaded using the backend gallery page only
`description` | string | Description metadata, available for images uploaded using the backend gallery page only
`sortOrder` | string | Image sort order, available for images uploaded using the backend gallery page only
`file` | [SplFileInfo](https://www.php.net/manual/en/class.splfileinfo.php) | A standard php file information object, only available for files uploaded using the Media Manager
`octoberImageFile` | [System\Models\File](https://github.com/octobercms/october/blob/master/modules/system/models/File.php) | A standard php file information object, only available for files uploaded using the Media Manager
`width` | integer| Image width, see https://www.php.net/manual/en/function.getimagesize.php
`height` | integer| Image height, see https://www.php.net/manual/en/function.getimagesize.php
`type` | string | Image type, see https://www.php.net/manual/en/function.getimagesize.php
`orientation` | string | Will be "horizontal", "vertical", or "square" depending on whether the image is wider than it is tall
`fileNameWithoutExtension` | string | Base name of the file without extension, for example: picture-1
`fileExtension` | string | [File extension](https://www.php.net/manual/en/splfileinfo.getextension.php), for example: jpg
`fileName` | string | [Filename](https://www.php.net/manual/en/splfileinfo.getfilename.php), for example: picture-1.jpg
`filePath` | string | [Path without filename](https://www.php.net/manual/en/splfileinfo.getpath.php), for example: <small>/var/www/mywebsite.com/public_html/storage/app/media/my-galleries/gallery-1</small>
`fileRealPath` | string | [Absolute path to file](https://www.php.net/manual/en/splfileinfo.getrealpath.php), for example: <small>/var/www/mywebsite.com/public_html/storage/app/media/my-galleries/gallery-1/picture-1.jpg</small>
`fileSize` | string | [File size](https://www.php.net/manual/en/splfileinfo.getsize.php), in bytes, for example: 404779
`relativeFilePath` | string | Path to file relative to the website, for example: <small>/storage/app/media/my-galleries/gallery-1/picture-1.jpg</small>
`uploaded` | string | [Last modified time](https://www.php.net/manual/en/splfileinfo.getmtime.php) for files uploaded using the Media Manager, or the upload time for files uploaded using the back-end gallery tab, you can then: $currentTime->format( 'c' );
`url` | string | URL to file, for example: <small>https://www.mywebsite.com/storage/app/media/my-galleries/gallery-1/picture-1.jpg</small>

<br>
<blockquote><p><strong>Hint:</strong> To dig into the <code>gallery.items</code> (or any other) variable/collection, you have two options. You can simply add <code>{{ dump(embeddedGallery.gallery.items.toArray) }}</code> on your page after the component definition and it will print debug information about that variable straight in your page. Alternatively, you can install the <a href="https://github.com/scottbedard/oc-debugbar-plugin">Debugbar plugin</a> and then add <code>{{ debug(embeddedGallery.gallery.items) }}</code> to your page to show debug information in the Laravel debugbar. To see all public properties of a galleryItem, do: <code>{{ debug(embeddedGallery.gallery.items.first.toArray) }}</code>. Make sure to replace "embeddedGallery" with the alias of your component as set in the component options!</p></blockquote>
<br>
customLightboxScript
**Additional Page Properties**

**`__SELF__.defaultgalleryoptions`**
Type: string
Used in the embedded gallery default template, this holds any custom script options set for the component in the "Script Options" property, along with any generated options (for example: `gallery_theme: "tiles", tiles_type: "justified"`)

**`__SELF__.defaultLightboxOptions`**
Type: string
Used in the lightbox gallery default template, this holds any custom script options set for the component in the "Script Options" property, along with the following: `gallery_theme: "lightbox"`

**`__SELF__.customgalleryscript`**
Type: string
The "Custom Gallery Script" set on the plugin backend settings page, if the "Custom Gallery Script" toggle switch is set to "ON".

**`__SELF__.customlightboxscript`**
Type: string
The "Custom Lightbox Script" set on the plugin backend settings page, if the "Custom Lightbox Script" toggle switch is set to "ON".

**`__SELF__.error`**
Type: string
If the plugin encounters an error, you can find the error description here.
</details>

# Known Issues

### Issue including CSS when used in a partial
OctoberCMS has a [known issue](https://stackoverflow.com/questions/53815815/on-octobercms-inject-css-from-partial) where if a component is dropped into a partial then any CSS that is added to the page by the partial is never actually rendered. This only occurs if the partial is directly inside of a layout, and if the `{% styles %}` tag is included before the partial.

Workarounds:

 - Add your `{% styles %}` *after* your `{% partial "..." %}`
 - OR Put your partial inside of a page, and include the page in the layout
 - OR Manually add the required CSS to your layout

# Support

Feel free to [file an issue](https://github.com/lieszkol/november-gallery/issues/new). Feature requests are always welcome.

If there's anything you'd like to chat about, please join the NovemberGallery  [Gitter chat](https://gitter.im/november-gallery/community)!

# License

This plugin is available in two editions: 

 1. The Personal Edition is a free plugin meant for non-profit use, such as:
	 2. Building a personal website that is not offering a product or services for sale
	 3. Academic use
	 4. Use by non-profit organizations
 2. The Professional Edition is meant for commercial use, such as:
	 1. A website selling or promoting products or services
	 2. Use by a for-profit organization

The professional edition is available from the OctoberCMS Marketplace. If you fit the criteria for the personal edition, then you are welcome to download it from GitHub and deploy it manually - as a free product we do not offer any support either with deployment or any issues you might encounter during use.

Commercial Use governed by the  [OctoberCMS Marketplace Purchased License](https://octobercms.com/help/license/regular)

# Credits / Major Dependencies

 - [UniteGallery jQuery Gallery Plugin](https://github.com/vvvmax/unitegallery)
 - [Swiper](https://idangero.us/swiper/)
 - OctoberCMS [Image Resizer plugin](https://octobercms.com/plugin/toughdeveloper-imageresizer)
 - [OctoberCMS]([https://github.com/octobercms/october](https://github.com/octobercms/october)) :-)

<p align="center">Created by <a href="http://www.lieszkovszky.com/" rel="nofollow">László Lieszkovszky</a> ❖ <a href="http://www.zensoft.hu/" rel="nofollow">ZenSoft Hungary</a></p>
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY5MjE5OTI3OSw2ODc3NzA5OTgsMTY5OD
A4MTg0NSwtMTA2MDY0NjE1NSwtOTQ5MzU3OTE0LDE3MjgzNTk4
ODYsLTY5NDU1Mjg1OSwtMTgyNTY1ODYzNiwtNzY4MTkxNTk0LC
0xNjYxMDQyOTk1LDYyNzMzODAwNiwtNTUwNjQ3NzgxLC05NjA2
ODc5MzUsLTU2MzkwNTE3NywtMTkzOTY5OTQyOSwzNDUwNjc3MT
MsMTQ3NjgyODI0MiwxNDIxMTc3MTksLTEyMDIyODIzMTcsLTMw
MDc2NTQxN119
-->