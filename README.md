# LA Metro Bus GTFS

## Latest Updates

### October 1, 2022

This update includes a new version of the June 2022 base GTFS.  It contains information about the new Line 857, a bus shuttle operating between the C (Green) and K (Crenshaw) rail lines. Service for Line 857 will begin on the opening day of the Crenshaw Line (October 7, 2022).

### June 2022 Shakeup

This GTFS update is for our June 2022 shakeup, effective June 26 - December 10.

### Dodger Stadium Express Update

This GTFS update adds on the 2022 Dodger Stadium Express service to February's shakeup.  Weekly `calendar_dates.txt` updates will require this update as a base.

### February 2022 Shakeup

This GTFS update is for our February shakeup, effective February 20 - June 25, 2022.  Our `stop_times.txt` file now contains the optional GTFS field `timepoint`.

### SoFI Stadium Express Update

We have been working with Swiftly to produce a GTFS-rt feed. One of the challenges for us was producing real-time cancellations at the trip level directly from our scheduling and daily operations software, HASTUS. The changes we made to the format of our trip_id was to accommodate both Swiftly as well as the Real Time Cancellation Export process. It now consists of the permanent_trip_id we introduced earlier, with the addition of a suffix denoting what service change this trip originates from.

This particular version also has SoFi Stadium Express service for the Super Bowl, as well.

As always, if you have issues with this feed, please send email to bakerro@metro.net

- LA Metro GTFS Team

### December 2021 Shakeup

This update's GTFS is active from Dec 19, 2021 to June 25, 2022.  It includes the previously released new permanent trip id format as well as some new fields.  If there are any issues, please email <a href="mailto:bakerro@metro.net">bakerro@metro.net</a>.

field|description
-----|-----------
`trip_id`|This is our old perm_trip_id followed by 6-7 character string delineating what shakeup it applies to (typically, something like '-DEC21' or '-SEPT21') This occurs in trips.txt as well as stop_times.txt
`trip_id_event`|This is our OLDER style trip number, maintained for people still using it. This occurs in trips.txt as well as stop_times.txt.
`route_code`|This is the trip_route, which was formerly only available in the stop_headsign field (Note: that this DIFFERS from the route_id, in that this is the route the trip is actually running, rather than the line it is scheduled off of (the route_id) This difference is mostly important for trips doing interlining or foreign line trips. Note: this can CHANGE in mid-trip, which is why we use stop_headsigns, rather than trip_headsigns. This value has been cleaned up somewhat, (the 'Change to' removed, as well as translated for some Route names currently expressed as letters). This field only occurs in stop_times.txt.
`destination_code`|This is the Trip's destination which was formerly only available in the stop_headsign field. This field has also been cleaned up somewhat, with some awkward abbreviations removed. This field only_occurs in stop_times.txt

### New Permanent Trip ID Format Released 11/4/21

Metro has been working with Swiftly to produce a GTFS-rt feed.  One of the challenges has been producing real-time cancellations at the trip level directly from HASTUS (our scheduling and daily operations software).  Changes were made to accommodate both Swiftly as well as the Real Time Cancellation Export process.  The `permanent_trip_id` now includes a suffix denoting what service change this trip originates from.  No changes were made to the September shakeup schedule.

Changes:

* `perm_trip_id` values are now appended with the shakeup they originated from, for example: `-SEPT21`
* Former `perm_trip_id` values are now listed under the `trip_id` field.
* Former `trip_id` values are now listed under a new `trip_id_event` field.

Examples:

__Old `stop_times.txt`__

trip_id|arrival_time|departure_time|stop_id|stop_sequence|stop_headsign|pickup_type|drop_off_type
-------|------------|--------------|-------|-------------|-------------|-----------|-------------
53820919-SEPT21-D15CAR-1_Weekday|5:42:00|5:42:00|2543|57|230 - Sylmar - Mission Coll|0|0
53820919-SEPT21-D15CAR-1_Weekday|5:43:00|5:43:00|2550|58|230 - Sylmar - Mission Coll|0|0
53820919-SEPT21-D15CAR-1_Weekday|5:44:00|5:44:00|3425|59|230 - Sylmar - Mission Coll|0|0
53820919-SEPT21-D15CAR-1_Weekday|5:45:00|5:45:00|3439|60|230 - Sylmar - Mission Coll|0|0
53820919-SEPT21-D15CAR-1_Weekday|5:47:00|5:47:00|3454|61|230 - Sylmar - Mission Coll|0|0
53820919-SEPT21-D15CAR-1_Weekday|5:48:00|5:48:00|3327|62|230 - Sylmar - Mission Coll|0|0
53820932-SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100|15:27:00|15:27:00|639|1|230 - Sylmar - Mission Coll|0|0
53820932-SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100|15:28:00|15:28:00|11416|2|230 - Sylmar - Mission Coll|0|0
53820932-SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100|15:29:00|15:29:00|11413|3|230 - Sylmar - Mission Coll|0|0
53820932-SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100|15:31:00|15:31:00|11398|4|230 - Sylmar - Mission Coll|0|0
53820932-SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100|15:32:00|15:32:00|11417|5|230 - Sylmar - Mission Coll|0|0

__New `stop_times.txt`__

trip_id|arrival_time|departure_time|stop_id|stop_sequence|stop_headsign|pickup_type|drop_off_type|trip_id_event
-------|------------|--------------|-------|-------------|-------------|-----------|-------------|-------------
<span style="color: red;font-weight: bold;">10230000950453-SEPT21</span>|5:42:00|5:42:00|2543|57|230 - Sylmar - Mission Coll|0|0|53820919-SEPT21-D15CAR-1_Weekday
<span style="color: red;font-weight: bold;">10230000950453-SEPT21</span>|5:43:00|5:43:00|2550|58|230 - Sylmar - Mission Coll|0|0|53820919-SEPT21-D15CAR-1_Weekday
<span style="color: red;font-weight: bold;">10230000950453-SEPT21</span>|5:44:00|5:44:00|3425|59|230 - Sylmar - Mission Coll|0|0|53820919-SEPT21-D15CAR-1_Weekday
<span style="color: red;font-weight: bold;">10230000950453-SEPT21</span>|5:45:00|5:45:00|3439|60|230 - Sylmar - Mission Coll|0|0|53820919-SEPT21-D15CAR-1_Weekday
<span style="color: red;font-weight: bold;">10230000950453-SEPT21</span>|5:47:00|5:47:00|3454|61|230 - Sylmar - Mission Coll|0|0|53820919-SEPT21-D15CAR-1_Weekday
<span style="color: red;font-weight: bold;">10230000950453-SEPT21</span>|5:48:00|5:48:00|3327|62|230 - Sylmar - Mission Coll|0|0|53820919-SEPT21-D15CAR-1_Weekday
<span style="color: red;font-weight: bold;">10230000951527-SEPT21</span>|15:27:00|15:27:00|639|1|230 - Sylmar - Mission Coll|0|0|53820932-SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100
<span style="color: red;font-weight: bold;">10230000951527-SEPT21</span>|15:28:00|15:28:00|11416|2|230 - Sylmar - Mission Coll|0|0|53820932-SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100
<span style="color: red;font-weight: bold;">10230000951527-SEPT21</span>|15:29:00|15:29:00|11413|3|230 - Sylmar - Mission Coll|0|0|53820932-SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100
<span style="color: red;font-weight: bold;">10230000951527-SEPT21</span>|15:31:00|15:31:00|11398|4|230 - Sylmar - Mission Coll|0|0|53820932-SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100
<span style="color: red;font-weight: bold;">10230000951527-SEPT21</span>|15:32:00|15:32:00|11417|5|230 - Sylmar - Mission Coll|0|0|53820932-SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100

__Old `trips.txt`__

route_id|service_id|trip_id|trip_headsign|direction_id|block_id|shape_id|perm_trip_id
--------|----------|-------|-------------|------------|--------|--------|------------
230-13149|SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100|53820932-SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100||0|2300902|2300095_SEPT21|10230000951527
230-13149|SEPT21-D15CAR-1_Weekday-NOHOHS1-0100000|53820933-SEPT21-D15CAR-1_Weekday-NOHOHS1-0100000||0|2300802|2300095_SEPT21|10230000951420
230-13149|SEPT21-D15CAR-1_Weekday-SAFEHB0|53820934-SEPT21-D15CAR-1_Weekday-SAFEHB0||1|2300702|2300091_SEPT21|10230000911408
230-13149|SEPT21-D15CAR-1_Weekday-SAFEHS1|53820935-SEPT21-D15CAR-1_Weekday-SAFEHS1||1|2301002|2300091_SEPT21|10230000911548


__New `trips.txt`__

route_id|service_id|trip_id|trip_headsign|direction_id|block_id|shape_id|trip_id_event
--------|----------|-------|-------------|------------|--------|--------|-------------
230-13149|SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100|<span style="color: red;font-weight: bold;">10230000951527-SEPT21</span>||0|2300902|2300095_SEPT21|53820932-SEPT21-D15CAR-1_Weekday-NOHOHS1-1011100
230-13149|SEPT21-D15CAR-1_Weekday-NOHOHS1-0100000|<span style="color: red;font-weight: bold;">10230000951420-SEPT21||0|2300802|2300095_SEPT21|53820933-SEPT21-D15CAR-1_Weekday-NOHOHS1-0100000
230-13149|SEPT21-D15CAR-1_Weekday-SAFEHB0|<span style="color: red;font-weight: bold;">10230000911408-SEPT21</span>||1|2300702|2300091_SEPT21|53820934-SEPT21-D15CAR-1_Weekday-SAFEHB0
230-13149|SEPT21-D15CAR-1_Weekday-SAFEHS1|<span style="color: red;font-weight: bold;">10230000911548-SEPT21</span>||1|2301002|2300091_SEPT21|53820935-SEPT21-D15CAR-1_Weekday-SAFEHS1
### 10/18/21 calendar_dates.txt

We have a special update to `calendar_dates.txt` today.  It includes an updated game time for the NLCS Game 3 (National League Championship Series) for the 10/19/2021 DSE (Dodger Stadium Express).

### 10/6/21 calendar_dates.txt

We've continued to adjust the process of posting the new weekly `calendar_dates.txt` file.  There is now a `notebooks\` folder in which we have a `calendar_dates.ipynb` Jupyter Notebook file and a `input\` folder with a `.zip` file for each week.  The notebook takes each of the weekly `calendar_dates.txt` files and applies them to the `calendar_dates.txt` from the Shakeup.  The resulting `calendar_dates\calendar_dates.txt` file can then *replace* the one in the main directory from the Shakeup.  Please [open an Issue](https://gitlab.com/LACMTA/gtfs_bus/-/issues) if you have any comments, questions, or run into any problems.

### 9/22/21 calendar_dates.txt

New `calendar_dates.txt` file uploaded to `calendar_dates\`.  This file covers the two-week span of 9/22/21-10/6/21.  To merge with the `calendar_dates.txt` file from the September shakeup, remove entries within that two week span and replace with the entries from the new file.

### Reverting calendar_dates.txt

We mistakenly replaced the September shakeup's `calendar_dates.txt` file with the weekly updated one.  This update reverts `calendar_dates.txt` to the full version from the shakeup.  The weekly updated version should be merged with the one from the shakeup.  It will be posted to the `calendar_dates/` folder for now.

### calendar_dates.txt update

A new `gtfs_bus.zip` file with an updated `calendar_dates.txt` file will be uploaded weekly.  This latest version corrects the previously uploaded `calendar_dates.txt` file, which had duplicate rows in it.

### September 2021 Shakeup

_Effective September 12, 2021_

Beginning with this shakeup, we will be updating the `calendar_dates.txt` file every ~2 weeks~ week to support the 100+ school calendars we track in order to provide service to schools.

Trips that occur irregularly, such as those supporting school schedules, we refer to as __Event__ trips.  Corresponding event codes are included in the `service_id` and `trip_id`.

This version of the GTFS has been modified to accomodate the new shakeup end date of December 18th, 2021.

### June 2021 Shakeup (update)

This minor update to the GTFS adds in the new SoFi Stadium Express (SSE) serving the new SoFi Stadium in Inglewood, CA.  We expect to release a new GTFS in 3 weeks for the September 2021 shakeup.

### June 2021 Shakeup (update)

_Effective July 18, 2021_ 

Line 152 - Changes to the turnaround loop.  Some new stops for these trips.

Line 236 - Approximately half of the trips will operate as a NEW Route 235 (uses the same `route_id` in the GTFS).  Some trip times will change.  Some trips will have some new stops.

NEW Line 622 - This will operate as an extension shuttle of the Line 222.  No changes to Line 222, but all trips on Line 622 are new.

Line 182 - The route has been modified for the turnaround loop currently being run under detour.  Some new stops.

No changes to the rest of service, including the Dodger Stadium Express (DSE).

### June 2021 Shakeup (minor changes)

This is a re-export of the base GTFS data for the June 2021 shakeup.  It includes the Dodger Stadium Express Service (DSE) as well as headsign changes for Line 207.

### June 2021 Shakeup

_Effective June 27, 2021_

This shakeup contains many major changes as part of Phase 2 of the NextGen bus system redesign.

### December 2020 Shakeup (minor changes)

Minor changes, including some shape cleanup.

### December 2020 Shakeup (Revised April 21)

_Effective April 21, 2021_

The GTFS has been updated with 2021 Dodger Stadium Express (DSE) Service.  Please note that the service will be on detour through the month of April and until May 11th, 2021.  During that time, service to the Union Station stop (`stop_id` 2155) will be instead be loading at Patsaouras Plaza, Bay No. 3 (`stop_id` 30000).  By May 11th, service will return to the westside of Union Station.  Detour details are being handled in the Alerts feed instead of the GTFS.

### December 2020 Shakeup (Revised April 12)

_Effective April 12, 2021_

There are 189 NEW trips over the December 2020 GTFS:

- 47 New Weekday Trips.
- 84 New Saturday Trips.
- 58 New Sunday Trips.

### December 2020 Shakeup

_Effective December 13, 2020_

This shakeup contains several major changes as part of Phase 1 of the NextGen bus project.

Please note that `trips.txt` now contains a new `perm_trip_id` field to assist with matching trips between the GTFS static and real time feeds generated by the ATMS (our CAD/AVL system). This permanent trip ID will be unique within a given shakeup.  The field is 14 characters long and is constructed as follows:

| Character | Description | Details |
|---|---|---|
| 1 | Day type of trip | 1 = Weekday <br>6 = Saturday <br>7 = Sunday |
| 2-5 | Line of trip | Padded with leading zeros |
| 6-10 | Pattern of Trip | Padded with leading zeros |
| 11-14 | Start time of trip | 36-hour clock in the format: `HHMM` |

HASTUS, our scheduling software, generates the pattern based on characteristics of the trip such as terminals, stops served, and direction of trip service.  All revenue trips will have a non-zero pattern while non-revenue trips will have a pattern of `00000`. Note that there will be no non-revenue trips in the GTFS.

Example:

> A permanent trip id of `10720002111821` indicates a trip that operates on a `weekday` on `Line 720`, using pattern `211` and starting at `6:21 pm`.

### October 2020 Shakeup

_Effective October 25, 2020_

This shakeup contains major changes for the L (Gold) Line due to the Little Tokyo/Arts District Station closure.
A new underground station will take its place as part of the Regional Connector Transit Project, due to open in 2022. In the meantime, shuttle bus service will run the segment of the L Line between Union Station and Pico/Aliso Station. Other lines, like the 30, contain updates to account for this change.

### June 2020 Shakeup (Revised July 27)

_Effective July 27, 2020_

This modification to the June 2020 Shakeup contains 32 additional weekday trips.

### June 2020 Shakeup (Revised July 7)

_Effective July 7, 2020_

This modification to the June 2020 Shakeup contains an update to Line 734, adding 8 more weekday trips. Due to ongoing evaluation of Metro's response to COVID-19, we expect to continue updating our service.

### June 2020 Shakeup (Revised June 24)

_Effective: June 24, 2020_

This is an update to the JUN20 Shakeup (the 200624 update, to be precise, in case there are others to come). In addition to the previous changes, this export has some corrections to the 90/91 route on about a dozen trips, one new weekday trip on the 166, and another new weekday trip on the 224.

Please address any questions to [bakerro@metro.net](mailto:bakerro@metro.net).

### June 2020 Shakeup

_Effective: June 21, 2020_

Changes include 2 trips added to the 207, fixing of Sunday calendars, fully implementing line letter changes (this applies to the [gtfs_rail](https://gitlab.com/LACMTA/gtfs_rail) as well), updates to line colors and line text colors, and updates to the route_urls to coincide with the new line letters.

### April 2020 Shakeup (Revised)

_Effective: April 26, 2020_

The April Shakeup has been revised to increase weekday service on some lines to relieve overcrowding.

### April 2020 Shakeup

_Effective: April 19, 2020_

This off-cycle shakeup has been instituted to deal with the effects of the COVID-10 coronavirus in Los Angeles.  We will be running modified service until a to-be-determined ending date. Instead of our normal Weekday, Saturday, and Sunday breakup, we will be running a Weekday Service and a combined Saturday/Sunday service.

## General Information

This is the General Transit Feed for LA Metro/LACMTA's complete bus service. For rail service, please see the [gtfs_rail](https://gitlab.com/LACMTA/gtfs_rail) repository.

As of May 6th, 2016 LA Metro has been publishing Bus and Rail Services as separate sets of GTFS files. They have been split up to allow the files to be updated more frequently.

Rail-only data is updated daily (generally Tuesday – Saturday mornings) and reflect all temporary rail service changes that may occur on a daily basis.

Bus-only data reflects large-scale changes to the system and occur approximately once every one or two months.

### gtfs_bus.zip Archive

The archive was created with this command on an BSD variant:

```bash
rm *zip
zip gtfs_bus *.txt
unzip -l gtfs_bus.zip
```

This command created a zip archive with these contents:

```bash
Archive:  gtfs_bus.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
      166  2022-06-03 13:51   agency.txt
     8049  2022-10-01 14:27   calendar.txt
   403651  2022-10-01 13:42   calendar_dates.txt
      283  2022-02-03 10:56   feed_info.txt
    11121  2022-10-01 13:43   routes.txt
 17571278  2022-10-01 13:45   shapes.txt
290610892  2022-10-01 13:50   stop_times.txt
   730889  2022-10-01 14:18   stops.txt
  3794245  2022-10-01 14:16   trips.txt
---------                     -------
313130574                     9 files
```

### Evergreen link to the zip archive: [https://gitlab.com/LACMTA/gtfs_bus/raw/master/gtfs_bus.zip](https://gitlab.com/LACMTA/gtfs_bus/raw/master/gtfs_bus.zip)

### Get the latest commit ID with Curl

```bash
#!/bin/sh

url="https://gitlab.com/LACMTA/gtfs_bus/commits/master.atom"

curl --silent "$url" | grep -E '(title>|updated>)' |   sed -n '4,$p' |   sed -e 's/<title>//' -e 's/<\/title>//' -e 's/<updated>/   /'       -e 's/<\/updated>//' |   head -2 | fmt

# returns:
# 2019-12-17T11:39:35-05:00
#    new info from SPA and instructions on preparing the archive
```

### Get the latest commit ID with Python

```bash
#!/bin/env python

import feedparser

url = 'https://gitlab.com/LACMTA/gtfs_bus/commits/master.atom'
d = feedparser.parse(url)
lastupdate = d['feed']['updated']

print lastupdate
```

---

See more developer resources at [Metro's Developer Site](https://developer.metro.net).

See the [Terms & Conditions](https://developer.metro.net/terms-conditions/) page for usage guidelines.
\n testttt
n testttt
testttt
testttt
\n testttt
\n testttt
\n testttt
test
\n testttt
\n testttt
\n testttt
