https://sensenet.sharepoint.com/Megosztott%20dokumentumok/Forms/AllItems.aspx?viewpath=%2FMegosztott%20dokumentumok%2FForms%2FAllItems%2Easpx&id=%2FMegosztott%20dokumentumok%2FDMS

## Register 

### Registration

* User opens app
* Clicks Register tab: /#/registration
* Provides following:
  * E-mail: zoltan.kultsar.sensenet@gmail.com
  * password: 5i8yfI7Nzo3Rvyr1Sj4P
  * confirmed password: 5i8yfI7Nzo3Rvyr1Sj4P
  * DISCUSS captcha: complete captcha. How...? :) Should we disable it?
* clicks Register

Result:
* user is created at backend
* user is added to [DISCUSS which groups]

### Login with newly registered user

* User opens app at https://sn-dms-demo-dev.netlify.com
* system redirects to https://sn-dms-demo-dev.netlify.com/#/login
* User types:
  * E-mail: zoltan.kultsar.sensenet@gmail.com
  * password: 5i8yfI7Nzo3Rvyr1Sj4P
* User clicks Login button

Result:
* User should be successfully logged in
* System redirects to https://sn-dms-demo-dev.netlify.com/#/documents/
* Private doclib should display


### Sign in with Google

DISCUSS: Google returns error 400, Error: redirect_uri_mismatch

## New - create new content in private workspace

* User clicks "Documents", then "+ New", then:
  * "New document". Window pops up, in which user enters/clicks:
    * Display Name: "e2e_document"
	* Watermark: "e2e_watermark"
    * Index: "10"
	* Clicks "Add reference". Reference picker window pops up, in which user clicks "Project"" / "Arizona Sales Workspace" / ".." / ".." / "Project" / "Budapest Project Workspace" / "Document Library" / "BusinessPlan.docx", then clicks OK.
	* Clicks "Submit"
  * New image
    * Description: "e2e description" in bold and italics --> DISCUSS/ADD ISSUE: currently this is the keywords field.
	* Date taken: "April 7th 09:10 pm"
    * Index: "10"
	* Width: 100
	* Height: 200
    * Display Name: "e2e_image"
	* Watermark: "e2e_watermark"
	* Clicks "Add reference". Reference picker window pops up, in which user clicks "Project"" / "Arizona Sales Workspace" / ".." / ".." / "Project" / "Budapest Project Workspace" / "Document Library" / "BusinessPlan.docx", then clicks OK.
	* Clicks "Submit"
  * New sheet
    * Display Name: "e2e_sheet"
	* Watermark: "e2e_watermark"
    * Index: "10"
	* Clicks "Add reference". Reference picker window pops up, in which user clicks "Project"" / "Arizona Sales Workspace" / ".." / ".." / "Project" / "Budapest Project Workspace" / "Document Library" / "BusinessPlan.docx", then clicks OK.
	* Clicks "Submit"
  * New slide
    * Display Name: "e2e_slide"
	* Watermark: "e2e_watermark"
    * Index: "10"
	* Clicks "Add reference". Reference picker window pops up, in which user clicks "Project"" / "Arizona Sales Workspace" / ".." / ".." / "Project" / "Budapest Project Workspace" / "Document Library" / "BusinessPlan.docx", then clicks OK.
	* Clicks "Submit"
  * New text
    * Display Name: "e2e_text"
	* Watermark: "e2e_watermark"
    * Index: "10"
	* Clicks "Add reference". Reference picker window pops up, in which user clicks "Project"" / "Arizona Sales Workspace" / ".." / ".." / "Project" / "Budapest Project Workspace" / "Document Library" / "BusinessPlan.docx", then clicks OK.
	* Clicks "Submit"
  * New folder
    * Folder name: "e2e_folder"
	* Clicks "Submit"

Result:
* Following contents are created:
  * /Root/Profiles/Public/alba/Document_Library/e2e_document.docx
  * /Root/Profiles/Public/alba/Document_Library/e2e_image.png
  * /Root/Profiles/Public/alba/Document_Library/e2e_sheet.xlsx
  * /Root/Profiles/Public/alba/Document_Library/e2e_slide.pptx
  * /Root/Profiles/Public/alba/Document_Library/e2e_text.txt
  * /Root/Profiles/Public/alba/Document_Library/e2e_folder
* with reference to /Root/Sites/Default_Site/workspaces/Project/budapestprojectworkspace/Document_Library/BusinessPlan.docx
* with the other properties above

 
## New - create new content in Budapest workspace

New document
New image
New sheet
New slide
New text
New folder












------ stuff to reuse -------

### Failed registration - passwords not identical, no password given or password strength/quality is not enough

### Register with Google auth 


### Login

* normal user
* workspace admin

### Logout




### Change workspaces

### Favourite workspaces

### Breadcrumb

* properly generated
* breadcrumb menu items
* navigate by clicking on breadcrumb parts

### New

* Create new content

### Upload

* Upload a single file
* Upload an empty file
* Upload a directory containing nested subdirectories, scattered with files and empty empty files
* Preview files with content
  * txt
  *  pdf
  * doc(x)
  * ...
* Preview empty files

### Download

* download single files
  * txt
  * pdf
  * doc(x)
  * ...

### Rename

* file
* folder

### Edit properties

* file

### Delete

* files
* folders

### Copy/Move

### Preview

* scrolling
* zooming
* jumping to pages

### Sharing

...

* Share
* Shared with me

### Versioning and Approval

These depend on background settings and your permissions, but more or less the following:
* Checkout: Lock doc. This should give a visible lock also. (Might modify something (eg. edit properties description)
* Undo checkout: This should revert the content to the state before you checked it out.
* Checkin
* Force undo checkout: unlock a document locked by another and throw away their changes.
* Publish: Create a new major version
* Approve and Reject

### Version history & restore

* view
* restore previous versions


## Users & Groups

### User page

* edit
* add to groups
* remove from groups


## Search

* Simple
* Advanced

### Saved queries

* save
* rerun
* delete

## General

* grid
  * ordering
  * selections
  * context menus
  * 3dot menus
* batch actions
* user menu
* message bar in bottom left corner

### Ordering in lists

