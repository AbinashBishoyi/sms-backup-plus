
#Analysing Android / ACRA error reports using the Google visualisation API

If you use [ACRA][] to monitor crashes in your
Android app you can easily check all error reports, inspect stack traces and so
on.

What's missing however is the big picture - are there more reported bugs on Android 1.x
than on 2.x ? Has the latest upgrade of your app improved the situation? Has the
Motorola DROID really the buggiest Android firmware on this planet?

Because ACRA uses Google Spreadsheet to store the data it is very easy to run
queries against it with the [Google Visualization API][]. The API has two
layers - a data access layer with a powerful [query language][] (similar to
SQL) and a lot of different components to visualise the data.

The interesting parts of the query language for this project are the `GROUP BY`
and `PIVOT` clauses. Getting crash counts for different application versions,
grouped by device models is very easy:

    SELECT model, COUNT(A) GROUP BY model PIVOT version

The results can now directly be used to create a new dynamic table or chart.

To use this for your own application take a look at [acra-analysis.html][] and
change the Spreadsheet link.  You will also need to set the sharing settings of
the spreadsheet to 'Anyone with the link' or 'public'. If this project evolves
further I'll eventually factor it out into a separate project.

## Rant

These analytic features should really be part of the Google Android dev console -
they own all the pieces to build it but then leave it to somebody else
The fact that an open source project (ACRA) is superior to the
built-in crash monitoring (which arrived really late) says it all.

## Live demo

Check out the current error stats of SMS Backup+: [Demo][]

## Screenshot

![Screenshot][]

## License

The code is licensed under the same conditions as [SMS Backup+][License].

[ACRA]: http://code.google.com/p/acra/
[acra-analysis.html]: https://github.com/jberkel/sms-backup-plus/blob/gh-pages/acra-analysis.html
[Google Visualization API]: http://code.google.com/apis/visualization/documentation/
[Screenshot]: https://github.com/downloads/jberkel/sms-backup-plus/acra-analysis-screenshot.png
[Demo]: http://jberkel.github.com/sms-backup-plus/acra-analysis
[License]: https://github.com/jberkel/sms-backup-plus#license
[query language]: http://code.google.com/apis/visualization/documentation/querylanguage.html
[SMS Backup+]: http://github.com/jberkel/sms-backup-plus
