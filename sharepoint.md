[Back](https://github.com/digiti/styleguides)
# SharePoint

## Naming & folder conventions
* All assets will be stored in the "Style Library" folder & follow a naming convention ```OPCO_projectname_filename.ext```.
* Fonts are stored in a seperate folder "fonts".
* Javascript files are stored in a folder "js". When you use a plugin/library which has a folder structure, please keep this folder structure in your project.
* Masterpages & page layouts need to be stored in the "Master Page Gallery".

### Images
Images are stored in the "Images" folder inside the "Style Library". Please put your images in a folder ```OPCO_projectname_Images``` to keep all image assets seperate for each project/subsite. 
Content specific images (banners, avatars, ...) will be stored in the appropriate folders in the default "Images" gallery which is located the root of each project or subsite.

## Best Practices

### Publishing assets
Checkin and/or publish the files you're working on **on a daily basis** or when you're done working on a certain project. 
If you don't do this, one of the following will happen:
* Your colleague (or the client/business) is confused when they don't see the changes you've made.
* Other people can't make changes to the files you've checked out to you.
* A kitten wil die every hour until your files are checked in or published! :cat2: :gun:

*Checked Out*: You're making changes to this file, so nobody else can access it.  
*Checked In*: The changes you've made will be visible the people with the same rights as you have.  
*Publish*: The changes you've made will be visible for everyone!

### Subsite templates
Make sure at the beginning of a project that only "Publishing Site" & "Blog" templates are available. **Do not use** subsite templates with a workflow. If a new environment is set up using a workflow you can easily remove them from the appropriate libraries (Page library, Master Page gallery, Style Library, ...).

### Masterpages & Page Layouts
Page layouts will be stored with the following attributes applied "Content Type Group" -> "Publishing Content Types" & "Content Type Name" -> "Page". In this way we can switch between every available page layout.

### Itemstyles
All itemstyles created will be prefixed with the project name (shorthanded) & grouped per subsite. By doing this it will be much easier to maintain or add new itemstyles when a new subsite needs to be created.

Best is to create one itemstyle template at a time & re-upload the "Itemstyles.xsl" file each time you've made a change. If you make one (tiny) mistake all Content Query Webparts will display an error message portal-wide. YOLO!

### Javascript
All Javascript files need to be included in the masterpage or page layout files. **Do not** attach Javascript files to a Content Editor Webpart, because every user with "Contribute" rights can easily remove those webparts...

The [SharePoint Services plugin](http://spservices.codeplex.com/) is a great library to communicate with the SharePoint Web Services via the SOAP protocol. Always make sure you have the right version in combination with the jQuery library. You can find more info on the project's homepage.

In case you are having issues with dragging & dropping webparts in a page layout, it's commonly caused by a position:relative on a parent wrapper. There is [an easy & quick fix](http://neilmosafi.blogspot.be/2007/11/sharepoint-dragging-webparts-causes.html) for that. You can just add the JS function to the portal's custom JS file.

### Search
In order to set up the out-of-the-box search functionality, we need to have "Site Collection Administrator Rights". When we have those rights we can configure the default search page & create a new "This Site" scope. **Do not mimic the search form**, unless you need to make a search results page per subsite.

### Archives
Archive pages will be set up using a default SharePoint view, unless specifically requested not to do so. 
Update the existing "Archive" view (or create one if not available by default) & group the elements per year. In order to do so you first need to create a calculated field with the follwing formula ```=TEXT(YEAR(Published),"000")```. If the archive page will not contain much items over time or there is no date field defined, then you can leave the year field out of consideration. 

### Files
When setting up a new portal use the following guides: Seperate words in a filename with dash. end the filename with versioning so when a second or third version of the portal will be made it's more clear wich version is the last. cfr: portal-1.0.js

### Cross Browser
Always make sure your project looks fine using the following browsers:
* IE 6 (only after specific request at the beginning of the project or during UAT)
* IE 7
* IE 8
* Google Chrome

Other browsers are not supported by default.

## Known Issues

1. It's not possible to edit Content Query Webparts on "dvl" environments. Best is to only set up the mainframe (materpage & page layouts) on "dvl" & make sure the project gets migrated to "staging" environment before you continue with implementation.
2. It's possible to use a multi-lookup field to tag/filter content. However it's not possible to print the field's content with an itemstyle.
