---
layout: post
title: "Requestly File Library"
excerpt: "Service to host your javascript and stylesheet files"
categories: documentation
sample: false
tags: [Requestly, Feature, Documentation, Library, Free Hosting]
comments: true
share: true
author: akhil_ojha
---

We have launched a new requestly service that manages your files.
You can upload your JS/CSS files with the help of this service and
get the url of uploaded file which you can use in requestly rules. To begin with this service supports only css and js files.

## Managing Your Files

### Login

When you navigate to the library service it will ask you to login using your google account.
This is required because we will internally be using your google drive to upload your files,
we will create a folder in your google drive and then use it to manage all files that you upload.

<figure>
  <a href="{{ site.baseurl }}/images/documentation/library-service/login.png">
  	<img src="{{ site.baseurl }}/images/documentation/library-service/login.png" alt="image">
  </a>
  <figcaption><center>Login Dialog</center></figcaption>
</figure>

### Upload File

Once you login you will be shown file list page with a message "You do not have any uploaded files".
You need to click on the upload button on top right corner to upload any file.
File explorer will open on clicking the button and you can select the file you want to upload.
(Right now we support only js and css files, we will extend this to all files soon)

<figure>
  <a href="{{ site.baseurl }}/images/documentation/library-service/upload.png">
  	<img src="{{ site.baseurl }}/images/documentation/library-service/upload.png" alt="image">
  </a>
  <figcaption><center>Upload Workflow</center></figcaption>
</figure>

### File Details

Once you have selected the file and its uploaded, we will show a dialog with file details.
Here you have option to copy the url of uploaded file, adding description for uploaded file and editing file content.
Same file detail dialog can be opened by clicking on the file name of any uploaded file.

<figure>
  <a href="{{ site.baseurl }}/images/documentation/library-service/filedetails.png">
  	<img src="{{ site.baseurl }}/images/documentation/library-service/filedetails.png" alt="image">
  </a>
  <figcaption><center>File Details</center></figcaption>
</figure>

To add/update description just click on the edit icon and add description for the file that you want to upload.
Once you are done, you can click the "green tick" button to add/update description.

<figure>
  <a href="{{ site.baseurl }}/images/documentation/library-service/filedetails_2.png">
  	<img src="{{ site.baseurl }}/images/documentation/library-service/filedetails_2.png" alt="image">
  </a>
  <figcaption><center>File Description</center></figcaption>
</figure>

### Content Editor

Similarly you can click on "Edit File Content" button to edit the file that you just uploaded,
we will open the file in our editor you that you can edit the file on fly.
Once you save file after editing we will update the content of the file but the "URL" for file will remain unaffected.

<figure>
  <a href="{{ site.baseurl }}/images/documentation/library-service/editor.png">
  	<img src="{{ site.baseurl }}/images/documentation/library-service/editor.png" alt="image">
  </a>
  <figcaption><center>Content Editor</center></figcaption>
</figure>

### File List

Once you have uploaded files, you can see them in the file list screen. Here you will have

- Name and description of all the files
- A button to copy url for the uploaded file.
- Edit icon button that will take you to editor and you can edit contents of that file.
- Delete icon button that you can use to delete the file.

<figure>
  <a href="{{ site.baseurl }}/images/documentation/library-service/fileindex.png">
  	<img src="{{ site.baseurl }}/images/documentation/library-service/fileindex.png" alt="image">
  </a>
  <figcaption><center>File List</center></figcaption>
</figure>

## FAQ

<div>
  <strong> Q: Can I use the Url of file in my Requestly rule ?</strong>
  <div>Yes, Absolutely! This is the central use case of Library Service. Host your local js,css files and get the Url.
    Use the url in Requestly rules.
  </div>
  <br/>
</div>

<div>
  <strong> Q: If I change file content, will the Url change ?</strong>
  <div>No, You can change file content as many times and your Url will be unaffected. This will make your debugging life easier.</div>
  <br/>
</div>

<div>
  <strong> Q: Can I directly add a file in my Google drive folder ? </strong>
  <div> No, Please do not modify the contents of Requestly folder in your Google drive.
  Let Library service do the heavy lifting for you. File upload, modification and deletion should be done only via Library service.
  </div>
  <br/>
</div>

For further questions, feel free to reach out at `requestly.extension@gmail.com` or tweet to `@requestly_ext`. Hope you like this feature.

## Links
- [Requestly Github Repo](https://github.com/requestly/requestly-issues){:target='_blank'}
- [Requestly on Chrome Store](https://chrome.google.com/webstore/detail/requestly/mdnleldcmiljblolnjhpnblkcekpdkpa){:target='_blank'}