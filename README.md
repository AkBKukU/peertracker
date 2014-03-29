#PeerTracker - Simple, Efficient and Fast BitTorent Tracker#

##What Do You Need?##
   - HTTP Web Server. Apache, Nginx, lighttpd etc., anything that supports PHP.
   - PHP 5+, Highly recommend the latest release or 5.3+, as it comes with SQLite3 ntegrated.
   - Database Support. Must use one of the following.
   - SQLite3 via PHP 5.3
   - MySQL 4.1+, Highly recommend the latest release or 5.1+. (Coming Soon)
   - PostgreSQL 8.0+, recommend the latest release or 8.4+. (Coming Soon)
   - txtSQL, Written entirely in PHP; performance is reflected in that. (Coming Soon)

###Optional###
   - .htaccess & mod_rewrite suppport. If you want to use /announce & /scrape without the .php file type extensions.


##Which Database System Should You Use?##
   
   - SQLite3
      - Pros:
         - Comes integrated with PHP 5.3.
         - Fantastic speed when using simple queries.
         - Single database file, no network connection overhead.
   - Cons:
      - Not designed for heavily loaded multi-user environments. I have not yet 
         tested this database system in a Real World Environment that experiences 
         several thousand Requests/s, but it should work fine for the typical tracker.
   - Summary:
      - Use this if you have a relatively small to medium sized tracker, and/or 
         don't have access to any of the other more robust database servers.

   - MySQL (Recommended), at least 4.1+, suggest 5.1+
      - Pros:
         - Performance is great all around.
         - Has been proven reliable and is production stable in multi-user environments.
         - Most common database used on the average non-corporate based website.
      - Cons:
         - Nothing significant as relates to it's use in PeerTracker.
      - Summary:
         - Use this database system if available. It's the most widely support database
         in shared hosting environments and any decent host offers them.

   - PostgreSQL (Coming Soon)
      - Pros: TODO
      - Cons: TODO
      - Summary: TODO


##Quick Install Guide##

PeerTracker is packaged in standalone versions. Each version is contained in it's 
own designated directory labeled by it's respectively used database system.

To setup MySQL for your tracker's database:

   1. Upload/help.php to your tracker's document directory.
   2. Upload all of the files inside of the mysql directory.
   3. Edit the configuration section at the top of the tracker.mysql.php file to have your database connection information.
   4. Run help.php from your browser and install the tracker database
   5. Remove help.php and you have now installed the MySQL edition of PeerTracker.

These same steps should be followed for whichever database system you choose to use.


##Step by Step Install Guide##

   1. Upload help.php to your tracker's document directory.
   2. Run the script from your site. (Ex: http://tracker.yoursite.com/help.php)
   3. Read the information in the table, this will let you know what database types your server supports.
   4. After deciding which database system you would like to use, upload the files inside
    of the respectively named directory to your tracker directory. (Ex: http://tracker.yoursite.com/announce.php, http://tracker.yoursite.com/scrape.php, etc)
   5. Edit the configuration file tracker.[Database Type].php. It contains all of the settings needed to connect to the database so you can run the tracker, such as path to the database, host, user, pass, port etc.
   6. .htaccess files are included, they allow PeerTracker to support the typical url 
    format (Ex: http://tracker.your.site/announce notice, no .php extension). Not 
    all webservers fully support these files. If you notice them causing any problems 
    just remove them, they're not necessary for tracker operation.
   7. Run help.php again, and proceed to install the tracker database.
   8. Delete help.php from your tracker's document directory.
   9. Finished tracker setup.

Now, you can use the following url for tracking:
`http://tracker.yoursite.com/announce`
Or the extended url, if your server doesnt support .htaccess files:
`http://tracker.yoursite.com/announce.php`


###SQLite3 Installation Notes###
Make sure to give write permissions 0777 to the 'DB' database directory or whichever 
directory you chose to store the SQLite3 Database file.

This is Required for PeerTracker to automate installation of database tables upon 
first use or after suffering a corruption. 
