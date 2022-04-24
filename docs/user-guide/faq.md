# Frequently Asked Questions

## General ##

??? question "When exactly will new features be released?"

    We have a zero bug policy and do our best to help users when they need support or have other questions.
    Updating and improving the documentation you are reading takes up a large part of our time too.

    This comes at a price, as we can't give exact deadlines for new features. Also keep in mind that epics
    like multi-user support can't be delivered in a single update. Working on big features is a continuous process
    that can take months to years until all use cases are covered.

    Having said that, funding really has the highest impact. So users can do their part and
    [become a sponsor](../funding.md) to get their favorite features as soon as possible.

??? question "Are there plans to introduce premium features?"

    PhotoPrism is 100% self-funded and independent. We plan to offer non-essential premium features and services as voluntary donations currently don't
    cover even our most basic expenses. It is in the best interest of all users that funding is sustainable
    in the long run.

    Unless your plan includes additional cloud storage, you will be able to upgrade and downgrade without
    losing any data. For those who don't like recurring subscriptions, there will be discounted multi-year / lifetime
    payment options. To account for income differences, pricing may also vary by region. As soon as we have
    details, we will announce them publicly.

    Meanwhile, GitHub Sponsors has [one-time donation](https://link.photoprism.app/donate)
    options if you don't need ongoing support after installation and don't expect updates with additional features
    for more than 12 months.

    We encourage everyone who can afford it to [become a sponsor](../funding.md) as this is ultimately best for
    the product and the community. Think of "free software" as in "free speech," not as in "free beer".

??? question "Why can't I just purchase and download a single version?"

    Offering single versions for one-time purchase without ongoing updates would be irresponsible.
    Unlike traditional offline apps such as Microsoft Office or single-player games, software exposed to the Internet
    must be updated regularly to stay secure and compatible with the latest standards.

    Updates are also important because virtually all file format parsers have flaws that just haven't been 
    discovered yet. This is a known risk that may affect you even if your computer isn't directly exposed to
    the Internet.

    It's essential to keep your operating system, Web browsers, and all other software up to date. Don't push your luck 
    and don't expect developers to spend time providing individual updates for old versions that contain only 
    critical security updates, but nothing else.

??? question "Will the self-hosted version continue to be supported once a hosted version is available?"

    Absolutely! Self-hosting is the easiest way to stay in control and protect [your privacy](https://photoprism.app/privacy) (a key part of our mission). It also provides the best experience for advanced users who often rely on a local toolchain to select, edit, and publish their pictures.
    
    We understand that there is a great demand and many practical uses for a hosted version, which we plan to offer in addition so that users have more choice. Selected hosting partners will ensure that the privacy of our users is protected as much as technically possible, even in the cloud.
    
    Likewise, businesses demand a commercial offering with features and support options geared towards professional users. They are willing to pay for the value they receive, which helps fund development and allows us to expand our team.

## User Interface ##

??? question "Can I use trees for organizing my pictures and albums?"

    Except in *Library > Originals* and for object classification in *Labels*, PhotoPrism does not
    support hierarchically organized content for a number of reasons:
    
    First, there are many tools (including Windows Explorer and Mac OS Finder) that already browse folders in such a way.
    
    A common UX challenge is dealing with namespaces.
    For example, the album "Berlin" may exist 5 times in different parts of a tree.
    To avoid ambiguities, simple input fields need to be replaced with a tree browser that
    shows the complete context.
    This is especially difficult on mobile screens.
    
    Personal albums can typically be browsed by time, with optional filters for more specific results.
    This is different in Enterprise asset management, where trees are required to manage
    responsibilities & [permissions](https://github.com/photoprism/photoprism/issues/455#issuecomment-675859270).
    We might do a special release for professional users later.
    
    While you have complete freedom with organizing your original files and folders,
    we don't think trees should be an integral part of our user interface.
    Most users won't be able to sort their memories in a strictly hierarchical way
    and prefer to explore them in multiple dimensions instead.

??? question "What's the difference between keywords and labels?"

    Keywords contain a list of search terms extracted from metadata, file names, and other sources
    like geodata. Pictures with matching keywords automatically show up in related *Labels*.

    Although related, keywords and labels serve different purposes:

    * **Labels** may have parent categories and are primarily used for classification, like "animal", "cat", or "boat". Duplicates and ambiguities should be avoided.

    * **Keywords** are primarily used for searching. They may include similar terms and translations, like "kitten", "kitty", and "cat".

??? question "Can I use the web interface to permanently delete files?"

    Yes, you can [permanently delete](./organize/delete.md) files.

## Search ##

??? question "Why can't I play live photos or find stacks when I search for specific images?"

    Our search API and user interface perform a file search. This is intentional since "stacks" can contain files of different types and properties, such as color.
    
    For example, there may be color and monochrome versions. Now, when you search for them or sort them by color, the user interface must display individual files. Otherwise, the results showing a color image/video when you filter by monochrome would make no sense.
    
    Likewise, if you search for `filename.mp4.*`, you will find only JPEGs without video, because the video file extension is `.mp4` without an extra dot at the end.

    We recommend using the `path:` and/or `name:` filters with wildcards if searching for individual files limits the search results too much. Most users will want to find all related files so that they can be displayed together, e.g. as live photos consisting of a video and an image.
    
    You can combine these filters with other filters such as `live` to ensure that the results include only pictures with a specific media type. Alternatively, you can use the `filename:` filter with a more permissive wildcard that excludes the file extension.

## Library, Counts & Files ##

??? question "What media file types are supported?"

    PhotoPrism supports indexing, viewing, and [converting](settings/library.md) most common image, video, 
    and RAW file formats, including JPEG, PNG, GIF, BMP, HEIF, HEIC, MP4, MOV, WebP, and WebM. 
    [TIFF is partially supported](https://github.com/golang/go/issues?q=is%3Aissue+image%2Ftiff+)
    without extensions like GeoTIFF.

    The internally used image format is JPEG. When indexing, a JPEG sidecar file can be created automatically for videos and images in other formats. It is needed for thumbnail generation, image classification, and face detection. JPEG XL support is planned as soon as it is generally available and enough compatible tools exist.
    
    If installed, converting RAW files is possible with the following converters (our Docker image includes both):

    - [Darktable](https://www.darktable.org/) ([supported cameras](https://www.darktable.org/resources/camera-support/))
    - [RawTherapee](https://rawtherapee.com/) ([supported cameras](https://www.libraw.org/supported-cameras))

    On a Mac, RAW files can also be converted with [Sips](https://ss64.com/osx/sips.html) ([supported cameras](https://support.apple.com/en-us/HT211241)).
    Our goal is to provide top-notch support for all RAW formats, regardless of camera make and model.
    Please let us know about any issues with a particular camera or file format.
    
    [Video formats](../developer-guide/media/index.md) supported by [FFmpeg](https://en.wikipedia.org/wiki/FFmpeg#Supported_codecs_and_formats) can be transcoded to
    [MPEG-4 AVC](https://en.wikipedia.org/wiki/Advanced_Video_Coding) for maximum browser compatibility. Still images for thumbnail creation can also be extracted from most videos.
    
    Make sure you have JSON sidecar files enabled if you have videos, live photos, and/or [animated GIFs](https://github.com/photoprism/photoprism/issues/590) so that video-specific metadata such as codec, frames, and duration can be extracted, indexed, and searched.

    For a complete list of file formats and extensions, see our downloadable [Feature Overview](https://link.photoprism.app/overview).

??? question "What metadata sidecar file types are supported?"

    Currently, three types of [file formats](../developer-guide/media/index.md) are supported:
    
    #### JSON ####
    
    If not disabled via `PHOTOPRISM_DISABLE_EXIFTOOL` or `--disable-exiftool`, [Exiftool](https://exiftool.org/) is used
    to automatically create a JSON sidecar for each media file. **In this way, embedded XMP and video metadata can also be indexed.**
    Native metadata extraction is limited to common Exif headers. Note that this causes small amount of overhead when
    indexing for the first time.
    
    JSON files can also be useful for debugging, as they contain the full metadata and can be processed with common
    development tools and text editors.
    
    *Metadata JSON files exported from Google Photos can be read as well. Support for more schemas may be added over time.*
    
    #### YAML ####
    
    Unless disabled via `PHOTOPRISM_DISABLE_BACKUPS` or `--disable-backups`, PhotoPrism automatically creates/updates
    [human-friendly YAML sidecar files](../developer-guide/technologies/yaml.md) during indexing and after manual
    editing of fields such as title, date, or location. They serve as a backup in case the database (index) is lost,
    or when folders are synchronized with a remote instance.
    
    Like JSON, [YAML](../developer-guide/technologies/yaml.md) files can be opened with common development tools and
    text editors. However, changes are not synchronized with the original index, as this could overwrite existing data.
    
    #### XMP ####
    
    XMP (Extensible Metadata Platform) is an XML-based metadata container format [developed by Adobe](https://www.adobe.com/products/xmp.html).
    It provides many more fields (as part of embedded models like Dublin Core) than Exif. This also makes it difficult - if not
    impossible - to provide full support. Reading title, copyright, artist, and description from XMP sidecar files is
    implemented as a proof-of-concept, [contributions are welcome](../developer-guide/metadata/xmp.md). Indexing of
    embedded XMP is only possible via Exiftool, see above.

??? question "Are JPEGs updated when RAW or XMP files change?"

    JPEGs are currently not regenerated when related RAW or XMP files change. RAW files are digital negatives by design. PhotoPrism therefore assumes that their image information is immutable.

    XMP files can affect the appearance, but most of the metadata they contain, such as title and description, does not. Creating JPEGs from RAW files is a time-consuming task, and in most cases would cause a huge, unjustified amount of overhead. In addition, the rendering information in XMP files is not well standardized. For example, changes you make in Photoshop may not be compatible with Darktable.

    We recommend manually updating existing JPEG sidecar files as needed or creating additional JPEGs, so you can choose between different versions. New files and other metadata changes are detected and reflected in the index as usual when your library is scanned.

??? question "Some files seem hidden, where are they?"

    If the [quality filter](organize/review.md) is enabled, you might find them in *Photos > Review*. Otherwise, their
    format may not be supported, they may be corrupted, or they may be stacked with other files if their name,
    exact date & location, or unique image ID indicate they belong to the same photo. You may then unstack
    them if this happened by mistake e.g. because of bad metadata.

??? question "For what reasons can files be stacked?"

    1. Files sharing exactly the same file and folder name will always be stacked, for example `/2018/IMG_1234.jpg` and `/2018/IMG_1234.avi`
    2. Files with related, sequential names like `/2018/IMG_1234 (2).jpg` and `/2018/IMG_1234 (3).jpg` may be stacked as well (optional)
    3. Pictures were taken at the same GPS position and second (optional)
    4. Image metadata contains the same *Unique Image ID* or *XMP Instance ID* (optional)

    You can change the behaviour for 2 - 4 in [*Settings*](settings/library.md).

??? question "I already indexed some files. Why are Folders, Calendar and Moments still empty?"

    Folders, Calendar and Moments are populated at the end of the indexing process.

??? question "Why does the count in *Search* not match the count of files in *Originals*?"

    *Library > Originals* shows actual files, whereas *Search* counts unique photos and videos.

    Photos and videos may have more than one file, for example:

    * A raw file + related jpg file + related xmp file = 3 files, 1 photo
    * A mp4 file + related jpg file = 2 files, 1 video

    It is also possible that multiple .jpg files are stacked because they are related to each other.

## Metadata ##

??? question "Why do some of my photos without geolocation information show a random location?"

    PhotoPrism estimates the location of photos without geolocation from photos that have been taken on the same day.
    You can disable estimations in [Settings](./settings/general.md).

??? question "Why do some pictures have an odd date like 01/01/1980?"

    This may happen in case there was an issue with your camera's settings when the photo was taken.
    While the date can easily be changed in the [edit dialog](organize/edit.md), this only updates the index
    without modifying your originals.
    
    To fix the date directly in your image or video files, please use other applications
    like Photoshop, or Exiftool, and re-index your library.

## WebDAV, Sync & Upload ##

??? question "Why do I get an error when trying to add a remote server for syncing?"

    When adding a new remote server, PhotoPrism tests a number of
    [common endpoints](https://raw.githubusercontent.com/photoprism/photoprism/develop/internal/remote/heuristic.go).
    Only when that fails, you'll see an error. There may be different reasons for this:

    - you are using HTTPS with an invalid certificate (not signed, outdated, domain doesn't match,...)
    - your server has permission issues, or an otherwise bad configuration. For example, Nextcloud blocks requests
    if the host doesn't match `trusted_domains` in its `config.php`
    - the IP is not reachable from your PhotoPrism instance due to network settings, or a firewall
    - the internal hostname can not be resolved to an IP address
    - it's the wrong host or port
    - username or password are wrong

    [Curl](https://curl.se/) is an excellent tool for
    [testing HTTP connections](https://code.blogs.iiidefix.net/posts/webdav-with-curl/) if you don't mind using a terminal:
    
    ```
    curl -X PROPFIND -H "Depth: 1" -u user:pass https://example.org/webdav/
    ```
    
    To avoid overlooking issues, it's best to run it from the same Docker container, virtual machine,
    or server environment where PhotoPrism is installed.

??? question "My file sync app fails with "unable to parse TLS packet headers" when trying to connect via WebDAV?"

    Because of security considerations, some backup tools and file sync apps like
    [FolderSync removed support for non-SSL HTTP communication](https://www.tacit.dk/foldersync/faq/#i-can-not-connect-to-a-non-https-webdav-server-why).
    
    If you install PhotoPrism on a public server outside your home network, **always run it behind a secure
    HTTPS reverse proxy**. Your files and passwords will otherwise be transmitted in clear text and can be intercepted 
    by anyone, including your provider, hackers, and governments. Backup tools and file sync apps may refuse to 
    connect as well.

*[sidecar files]: additional files that sit next to a main file
