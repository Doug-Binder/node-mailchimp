node-mailchimp
==============

A node.js wrapper for the MailChimp API. 

All functions of the MailChimp API (Version 1.3) and the MailChimp Export API
(Version 1.0) as described on [http://www.mailchimp.com/api/](http://www.mailchimp.com/api/) 
are exposed to your node.js application.

Installation
------------

Installing using npm (node package manager):

    npm install mailchimp
    
If you don't have npm installed or don't want to use it:

    cd ~/.node_libraries
    git clone git://github.com/gomfunkel/node-mailchimp.git mailchimp

Usage
-----

More or less proper documentation can be found in the source code. Available
API functions and their documentation can be found on 
[http://www.mailchimp.com/api/](http://www.mailchimp.com/api/). You can also
find further information on how to obtain an API key and much more on the 
MailChimp API pages.

MailChimp API:

    var MailChimpAPI = require('mailchimp').MailChimpAPI;
    
    var apiKey = 'Your MailChimp API Key';
    
    try { 
        var api = new MailChimpAPI(apiKey, { version : '1.3', secure : false });
    } catch (error) {
        console.log('Error: ' + error);
    }
    
    api.campaigns({ start: 0, limit: 25 }, function (data) {
        if (data.error)
            console.log('Error: '+data.error+' ('+data.code+')');
        else
            console.log(JSON.stringify(data)); // Do something with your data!
    });
    
    api.campaignStats({ cid : '/* CAMPAIGN ID */' }, function (data) {
        if (data.error)
            console.log('Error: '+data.error+' ('+data.code+')');
        else
            console.log(JSON.stringify(data)); // Do something with your data!
    });
    
MailChimp Export API:

    var MailChimpExportAPI = require('mailchimp').MailChimpExportAPI;
    
    var apiKey = 'Your MailChimp API Key';

    try { 
        var api = new MailChimpExportAPI(apiKey, { version : '1.0', secure: false });
    } catch (error) {
        console.log('Error: ' + error);
    }

    exportApi.list({ id : '/* LIST ID */'  }, function (data) {
        if (data.error)
            console.log('Error: '+data.error+' ('+data.code+')');
        else
            console.log(data); // Do something with your data!
    });

ToDo / Ideas
------------

 * Implement API versions 1.1 and 1.2
 * Implement WebHooks
    
License
-------

node-mailchimp is licensed under the MIT License. (See LICENSE) 