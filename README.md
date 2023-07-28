# Help a Paw Website
## Tools used to design site
- Mobirise website designer tool app for PC/Mac (free version) 
- Free HTML Code Editor extension for Mobirise that let's you edit the source:  https://witsec.nl/extension-code-editor.html

## Services used to run site
- Cloudflare:  CDN/web host  (free version)
- Github (free version):  Where you are reading this now!  While you can upload the website source directly to Cloudflare, you can't download it so it doesn't serve as a good home/shared space for the source.  Its not as feature rich as well.   Also, nice to have a backup/separate copy somewhere else.
 
##  Structure of code here at git
- The root folder cointains the published/rendered-if-you-will website files.  This is what cloudflare serves up.
- The mobirise source is in a file called "mobirise-source.zip".   This source is downloadable/editable on a PC/Mac using the free Mobirise app.   I'm storing the source and the published html files both in the same repo because the site is so small.  A separate repo would have been superfluous. 

## What's inside the mobirise-source.zip file
- Mainly the mobirise project file/assets which are used to create the final html/js/css and images
- And also a folder called "additional-pages".  This folder contains privacy_policy.html, apple-app-site-association and backup copy of the signal pages in case the current ones get messed up
- I created mobirise-source.zip by using Mobirise's export feature to export the files into c:\temp then added the additional-pages folder from a previous copy/release
- And there is also folder called original source images just in case they are useful for future improvements

## Its actually two sites, an english site and a bulgarian site
- Ideally we should just have one website source tree/mobirise project file but part of mobirise's charm is its limitations.  One of its limitations is that it must share the same header accross all pages in its site/project.
- So we couldn't have both an english header and bugariant header (top nav)
- So the workaround is to publish the sites on top of each other.  Since they are the exact same sites basically, there is no conflict.  They share the same images just fine.
- English site "Help a Paw" Mobirise - containts the English site in a single page (index.html) plus the assets folder (mainly images).  It also includes these extra pages: install.html, install_en.html, signal.html, signal_en.html, logo.html and the apple-app-site-association file (which has no extension).
- Bulgarian site "Help a Paw Bulgarian" Mobirise source (which essentially just results in the index_bg.html file) - this had to be separate because Mobirise wont let you have a different topnav for a page inside the english site.  So a separate site was required.   This is no big deal, but requires a two step process when publishing (described further below).   This site has the same assets folder as the english site so they can be published on top of each other (aka into same folder) w/ no conflict which creates the complete EN and BG sites.
- Its kind of 3 sites in a way, when you consider the additional-pages files also need to be saved to the website root and these additional-pages are not included in the mobirise source

## Website Publishing process - (from Mobirise to Git to Cloudflare)
1. Using Mobirise,  Publish the english (Help a Paw) site to a local folder,  like c:\temp
2. Make sure that folder is empty
3. Then publish the Bulgarian site (Help a Paw Bulgarian) site (which is just index_bg.html) to c:\temp.   Since it shares the same assets this will be the only file that really gets published.
4. From the "extra html pages" folder in the source copy privacy_policy.html and apple-app-site-association (has no extension) to c:\temp.   THIS IS ONLY NECC IF THERE WAS A CHANGE TO THESE FILES OR IF STARTING OVER WITH A CLEAN REPO.
5. If you know GIT, there is probably a proper git command to publish from here, but since I don't, i'll give you the simpleton method:  from the github home (https://github.com/HelpAPaw/Website) click Add File, then upload files, then drag and drop everything inside c:\temp over to github
6. Make sure to hit the Commit button after the uploads are complete
7. A few mins later,  Cloudflare will pick up the changes and update itself.

## Mobirise Source Code Publishing proces
There is probably a better way of doing this, but for now...
- Clear out a folder like c:\temp, create a folder called "bulgarian mobirise source" and "english mobirise source
- In Mobirise,  Export the English source by going to Sites in the left nav, then settings icon, then Export the source to c:\temp\english mobirise source
  - Note the Mobirise quirk where the settings icon doesn't show up unless that site was already loaded in the editor
- Repeat the above for the bulgarian site
- Copy the additional-pages folder and original source images folder from a prior release over to c:\temp so everything is in one place
- Zip everything up into mobirise-source.zip and publish it to git like in step 5 in the above process


# Details details details

## install.html, install_bg.html 
- these pages are not linked to by the website
- they are pages linked to from the "outside"
- they exist in the english "Help a Paw" site/source (vs the Help a Paw Bulgarian site)

## signal.html, signal_bg.html 
- these pages are not linked to by the website, they are pages linked to from the "outside".  
- They are shown as "signal" and "signal bg" in the Help a Paw english source
- IMPORTANT: You should not need to modify these , but if you do modify them in Mobirise (perhaps to fix grammar or change the text or images) then you will need to modify them manually with a text editor (or the Code Editor extension) to make sure the javascript QRCode generator still works - see "Modifying Signal Pages" section below.  Test locally to see if signal.html and signal_bg.html create QR Coodes.

## privacy_policy.html
- This is required by Apple or Google,  it is not included in the Mobirise source as it is a plain html file

## apple-app-site-association (has no extension) 
- This is required for Apple, it is not included in the Mobirise source,  no need to edit/worry about it except make sure to keep it published to the website.  Copy it 

## Source Backups/ability to revert
Revert (undo) isn't really built into Mobirise, but you can export the source as often as you want.  And I do occasionally.  Go to Sites on the leftnav, then over on a site, click gear icon and click Export.   


## Mobirise configuration
- help.a.paw@outlook.com is setup for receiving contact us form submissions/messages.   It uses a 3rd party service via  https://formoid.net/ to send the email so may need to add this to your address book to clear spam issues
- To share the Mobirise source with a collaborator, go to Site Settings->Export Project.  The source is a combination of the project.mobirise file and the assets folder
- Aformentioned extention at the top of this readme

## Cloudflare quirks
- Don't set CNAME for helpapaw.org or dont set www.helpapaw.org when using cloudflare pages because when you use cloudflare pages it wants to set these themselves and they interfere when you do it manually.  You have to use Cloudflare pages "custom domain" feature/setting to set each of these domains up.  (One setting for both).   Now that it is setup, shouldn't have to deal with this, just FYI
- Cloudflare has two products:  Cloudflare Pages and "Custom Pages".  It gets confusing.  We're using Cloudflare Pages which is accessed via the initial home screen, left nav ->  Workers and Pages

##  Modifying Signal Pages ("signal" or "signal bg" as called via Mobirise, and signal.html and signal_bg.html once published)
Again, you shouldn't need to update these pages, but if you do then you will need to edit their html after publishing as follows:

1. After the first </head> line in the html (about line 30),  delete the line that says <body> 
2. Where <body> was,  insert the following html:
<body onload="addQrImage()">
    <script>
      function addQrImage() {
        var urlSearchParams = new URLSearchParams(window.location.search);
        console.log(window.location.search);
        var params = Object.fromEntries(urlSearchParams.entries());
        console.log(params);

        var image = document.createElement("img");
        var imageParent = document.getElementById("qrImageParent");
        image.id = "qrImage";
        image.className = "class";
        image.src =
          "https://chart.googleapis.com/chart?cht=qr&chs=300x300&chl=" +
          params["link"];
        imageParent.appendChild(image);
      }
    </script>
3. Look for the text "QRCODE" and remove it
4. Where that word was, insert the following html:  <p style="max-width: 250px;" id="qrImageParent"></p>
