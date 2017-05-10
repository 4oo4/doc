# Migrate from ...

In wallabag 2.x, you can import data from:

-   [Pocket](#id1)
-   [Readability](#id2)
-   [Instapaper](#id4)
-   [wallabag 1.x](#id6)
-   [wallabag 2.x](#id7)

We also developed [a script to execute migrations via command-line
interface](#import-via-command-line-interface-cli).

Because imports can take ages, we developed an asynchronous tasks
system. [You can read the documentation
here](http://doc.wallabag.org/fr/master/developer/asynchronous.html)
(for experts).

## Pocket

### Create a new application on Pocket

To import your data from Pocket, we use the Pocket API. You need to
create a new application on their developer website to continue.

-   Create a new application [on the developer
    website](https://getpocket.com/developer/apps/new)
-   Fill in the required fields: application name, application
    description, permissions (only **retrieve**), platform (**web**),
    accept the terms of service and submit your new application

Pocket will give you a **Consumer Key** (for example,
49961-985e4b92fe21fe4c78d682c1). You need to configure the
`pocket_consumer_key` in the `Config` menu.

Now, all is fine to migrate from Pocket.

### Import your data into wallabag 2.x

Click on `Import` link in the menu, on `Import contents` in Pocket
section and then on `Connect to Pocket and import data`.

You need to authorize wallabag to interact with your Pocket account.
Your data will be imported. Data import can be a demanding process for
your server.

## Readability

### Export your Readability data

On the tools
([<https://www.readability.com/tools/>](https://www.readability.com/tools/))
page, click on "Export your data" in the "Data Export" section. You will
received an email to download a json (which does not end with .json in
fact).

### Import your data into wallabag 2.x

Click on `Import` link in the menu, on `Import contents` in Readability
section and then select your json file and upload it.

Your data will be imported. Data import can be a demanding process for
your server.

## From Pinboard

### Export your Pinboard data

On the backup
([<https://pinboard.in/settings/backup>](https://pinboard.in/settings/backup))
page, click on "JSON" in the "Bookmarks" section. A JSON file will be
downloaded (like `pinboard_export`).

### Import your data into wallabag 2.x

Click on `Import` link in the menu, on `Import contents` in Pinboard
section and then select your json file and upload it.

Your data will be imported. Data import can be a demanding process for
your server.

## From Instapaper

### Export your Instapaper data

On the settings
([<https://www.instapaper.com/user>](https://www.instapaper.com/user))
page, click on "Download .CSV file" in the "Export" section. A CSV file
will be downloaded (like `instapaper-export.csv`).

### Import your data into wallabag 2.x

Click on `Import` link in the menu, on `Import contents` in Instapaper
section and then select your CSV file and upload it.

Your data will be imported. Data import can be a demanding process for
your server.

## wallabag 1.x

If you were using wallabag v1.x, you need to export your data before
migrating to wallabag v2.x, because the application and its database
changed a lot. In your old wallabag installation, you can export your
data, which can be done on the Config page of your old wallabag
installation.

![Exporting from wallabag v1](../../img/user/export_v1.png)

If you have multiple accounts on the same instance of wallabag, each
user must export from v1 and import into v2 its data.

If you encounter issues during the export or the import, don't hesitate
to [ask for support](https://gitter.im/wallabag/wallabag).

When you have retrieved the json file containing your entries, you can
install wallabag v2 if needed by following [the standard
procedure](http://doc.wallabag.org/en/master/user/installation.html).

After creating an user account on your new wallabag v2 instance, you
must head over to the Import section and select Import from wallabag v1.
Select your json file and upload it.

![Import from wallabag v1](../../img/user/import_wallabagv1.png)

## wallabag 2.x

From the previous wallabag instance on which you were before, go to
All articles, then export these articles as json.

![Export depuis wallabag v2](../../img/user/export_v2.png)

From your new wallabag instance, create your user account and click on
the link in the menu to proceed to import. Choose import from wallabag
v2 and select your json file to upload it.

If you encounter issues during the export or the import, don't hesitate
to [ask for support](https://gitter.im/wallabag/wallabag).

# Import via command-line interface (CLI)
---------------------------------------

If you have a CLI access on your web server, you can execute this
command to import your wallabag v1 export:

```bash
bin/console wallabag:import username ~/Downloads/wallabag-export-1-2016-04-05.json --env=prod
```

Please replace values:

-   `username` is the user's username
-   `~/Downloads/wallabag-export-1-2016-04-05.json` is the path of your
    wallabag v1 export

If you want to mark all these entries as read, you can add the
`--markAsRead` option.

To import a wallabag v2 file, you need to add the option
`--importer=v2`.

If you want to pass the user id of the user instead of it's username,
add the option `--useUserId=true`.

You'll have this in return:

```
Start : 05-04-2016 11:36:07 ---
403 imported
0 already saved
End : 05-04-2016 11:36:09 ---
```
