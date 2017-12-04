# GoogleSheetsFitBitData

I've consolidated code found elsewhere that wasn't being updated anymore (since 2015) to pull down personal data from the FitBit API to Google Sheets. 

Specifically, I used it from this: https://github.com/loghound/Fitbit-for-Google-App-Script I'm also working on merging in the outstanding pull requests that are languishing, and I'll try to update the Google OAuth so you can use the latest version instead of languishing in version 19.  

For now, here's the (overly) detailed steps to get this going, assuming you've done nothing to start:

1. Create a new Google Spreadsheet
1. Set up the fitbit.gs code in Script Editor
   * Go to Tools -> Script Editor
   * Replace the code.gs with fitbit.gs and save

1. Add the OAuth Library in Script Editor (Documented here: https://github.com/googlesamples/apps-script-oauth2/tree/0e7bcd464962321a75ccb97256d5373b27c4c2e1#setup)
   * Go to to Resources -> Libraries...
   * In the "Find a Library" text box, enter the project key "MswhXl8fVhTFUH_Q3UOJbXvxhMjh3Sh48" and click the "Select" button.
   * Choose choose version 19 in the Version dropdown. Click Save.

1. Get Information About the Project
   * Go to File -> Project Properties
   * Under the Info tab, make note of the value in Project Key (Deprecated)
  
1. Assemble your Redirect URI (Documented here: https://github.com/googlesamples/apps-script-oauth2/tree/0e7bcd464962321a75ccb97256d5373b27c4c2e1#redirect-uri)
   * Add your project key from above step to this URL https://script.google.com/macros/d/{PROJECT KEY}/usercallback
  
1. Set up your FitBit Dev Credentials (if you haven't already)
   * In a new tab, log into FitBit dev site with your FitBit credentials: https://dev.fitbit.com/apps/new
   * Fill in whatever you want for App Name, Description, Website, Organization and Organization Website (the two websites do need to have full URL, such as http://www.example.com but the URLs themselves don't matter)
  * Select 'Personal' for OAuth 2.0 Application Type
  * For the Callback URL, enter the URL you put together with your project key (https://script.google.com/macros/d/{PROJECT KEY}/usercallback)
  * Select 'Read-Only' for Default Access Type
  * Agree to Terms of Service and click Register
  * Make note of the FitBit Cliend ID and FitBit Client Secret
 
1. Configure Spreadsheet
   * Navigate back to your Google spreadsheet itself and refresh. A new FitBit menu item should appear in the bar.
   * Go to FitBit -> Configure 
   * Enter the FitBit Client ID, FitBit Client Secret, and Google Project ID
   * Select the resources you want and the time period you want
   * Ignore the paragraph of text before the options, these steps were covered in what I wrote out above
   * Save Configuration
  
1. Authorize the Application
   * Still on the spreadsheet, go to FitBit -> Authorize
   * Side bar will open on the sheet. Click the link to Authorize.
   * Accept the FitBit scope authorization in the new window
   * Close and return to the spreadsheet

1. Pull down data
   * On the spreadsheet, go to FitBit -> refresh Tidbit Time data
   * Watch in awe as data populates on the sheet
