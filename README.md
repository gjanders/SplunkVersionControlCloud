# Splunk Version Control Cloud

## What does this app do?

This application is the simplified version of the Splunk Version Control application (VersionControl For Splunk on SplunkBase)

This application provides the dashboards, saved searches, macros and lookups required to allow a remote backup from the Splunk Version Control application. Note that this application does not remove the requirement for a Splunk enterprise instance running remotely to run the backup/restore.

## Why?
The full application contains python code that would not work within the SplunkCloud environment, this simplified version contains no python code or custom commands. The full application can run remotely to complete the backup/restore as required.

## How do I use this application? 

The dashboard within the application is only useful when the Splunk Version Control application is up and running remotely to create backups and trigger restores, please refer to the SplunkBase and github links below to install the VersionControl For Splunk on a non-SplunkCloud Splunk instance

## SplunkBase Links
[VersionControl For SplunkCloud](https://splunkbase.splunk.com/app/5061)

[VersionControl For Splunk (full app for backup/restore)](https://splunkbase.splunk.com/app/4355)

## Github Links
[SplunkVersionControl github](https://github.com/gjanders/SplunkVersionControl)

[SplunkVersionControlCloud github](https://github.com/gjanders/SplunkVersionControlCloud)

## How does this compare with other version control apps for Splunk?
As of October 2022, there are still no signs of version control within the Splunk Enterprise (or cloud) product, however you do have a few options in terms of a version control app, these include:
- [Git Version Control for Splunk](https://splunkbase.splunk.com/app/4182) - this app provides a modular input to help with getting configuration into a git repository from the filesystem. Note: on-prem instances only, no Splunk Cloud support.
- [FN1315 - Cover Your Assets: Protect Your Knowledge Objects from Yourself (and Others) - A Paychex story github](https://github.com/paychex/Splunk.Conf19) - this git location provides a list of searches that produce curl commands you can use to restore objects. This can work on-prem or in Splunk Cloud
- [Splunk2Git](https://github.com/paychex/splunk-python/tree/main/Splunk2Git) - Paychex's script to move Splunk knowledge objects into git using REST API
- [Version Control for Splunk](https://splunkbase.splunk.com/app/4355) - this app uses the REST API to download configuration and store inside a git repository in JSON format. Supports restoration of objects via dashboard (no admin support required). This can work on-prem or on Splunk Cloud remotely (this app runs on prem)
- [VersionControl for SplunkCloud (this app)](https://splunkbase.splunk.com/app/5061) - these are the dashboards and savedsearches that are installed on the SplunkCloud instance to support the version control app running remotely
- [Search Head Backup](https://splunkbase.splunk.com/app/6438) - backup to an index, works in Splunk Cloud

## Splunk alternatives
Or if the idea [Source Control on ideas.splunk.com](https://ideas.splunk.com/ideas/E-I-7) is implemented then this app will be replaced by this functionality..

## Release Notes 
### 0.0.9
README.md update

### 0.0.8
Updated the savedsearches for the `_audit` index query to look for info=completed as well as info=granted, as this does not appear in Splunk 9
Updated the splunk restore dashboard to mention that wildcards are now supported for restoration

### 0.0.7
Updated metadata file to allow `sc_admin` role read/write access

### 0.0.6
Updates to dashboards:
`splunkversioncontrol_restore.xml`

To provide a drop down list of available knowledge objects in addition to the text field option

Updated reports:
`SplunkVersionControl CheckAdmin` - simplified to use the Splunk users list

`splunk_vc_kom_audit_summary` - updated to ignore the manager URI's and handle proxied REST calls from the KOM report

### 0.0.5
Added a new macro `splunk_vc_ko_query` and a new savedsearch `splunk_vc_kom_audit_summary`
This relates to new functionality in the [VersionControl For Splunk (full app for backup/restore)](https://splunkbase.splunk.com/app/4355) app

Added the version=1.1 flag inside the dashboards for Splunk 8.2 compatability

### 0.0.4
Updated the `splunkversioncontrol_globalexclusionlist.csv` lookup to exclude an additional cloud specific app

### 0.0.3
Updated the `splunkversioncontrol_globalexclusionlist.csv` lookup to exclude various cloud specific apps

### 0.0.2
README.md update only

### 0.0.1
Initial version
