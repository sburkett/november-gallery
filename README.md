

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

Please see the [NovemberGallery manual](https://its.zensoft.hu/books/november-gallery-cookbook/page/installation-deployment)!

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
eyJoaXN0b3J5IjpbLTE1MzY2MjI2MTksLTE5MzIxNDk0NDAsLT
U3ODExMzg3Niw2ODc3NzA5OTgsMTY5ODA4MTg0NSwtMTA2MDY0
NjE1NSwtOTQ5MzU3OTE0LDE3MjgzNTk4ODYsLTY5NDU1Mjg1OS
wtMTgyNTY1ODYzNiwtNzY4MTkxNTk0LC0xNjYxMDQyOTk1LDYy
NzMzODAwNiwtNTUwNjQ3NzgxLC05NjA2ODc5MzUsLTU2MzkwNT
E3NywtMTkzOTY5OTQyOSwzNDUwNjc3MTMsMTQ3NjgyODI0Miwx
NDIxMTc3MTldfQ==
-->