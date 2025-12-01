---
title: 2025 Illegal Boat Strikes
date: 3025-00-00 00:00:00 -0700
style: post
author: the.fedora
---
## Background
> Since I started researching and writing this post, credible sources have reported that *survivors* of the first strike were [intentionally targeted, on Hegseth's orders](link). This was apparently covered up by claiming the second strike on the already-destroyed boat was to clear it as a navigation hazard (WTF?!). While multiple observers already labeled these strikes illegal, this seems to clinch that conclusion.

Since September 1, 2025, the current U.S. administration has been conducting *questionably legal* attacks on small vessels in the Caribbean and Pacific, which they claim to be "narco-terrorists". This has resulted in ... persons killed with no due process, and despite the administration's protests otherwise, this may well fall afoul of both domestic and international law. The primary source for information on these attacks has been social media posts by the administration, with flashy visuals and not much else. But it does offer a timeline, and that opens the door to more closely tracking these actions. .... on [r/OSINT](www.reddit.com/r/OSINT) has suggested that firewatch data from NASA might show these strikes, making a reasonable case that a [Visible Infrared Imaging System (VIIRS)](link) detection at ... corresponds to a known strike from 27 October. This is based on that VIIRS detection falling in the appropriate range given by Mexican Search and Rescue (SAR), and the intermittent nature of the detection suggesting that it is not a regular/industrial thermal event such as an oil rig flare.

Wikipedia editors have been maintaining a [list](link) of these boat strikes, so in theory it should be possible to apply similar methodologies to isolate candidate strike locations for many if not all of them. The Wikipedia table is reproduced below:

idx,date,location,no_vessels,killed,captured,missing,sources/notes
1,1 September 2025,Caribbean – Venezuela,1,11,,,Most sources list as 2 September;[12] Venezuelan sources state vessel was struck the day before[19]
2,15 September 2025,Caribbean – Venezuela,1,3,,,Gustavo Petro alleges one casualty was a Colombian fisherman[12][38]
3,19 September 2025,Caribbean,1,3,,,Dominican Republic recovers cocaine[12][61]
4,3 October 2025,Caribbean – Venezuela,1,4,,,First strike after notification of "armed conflict"[12][53]
5,14 October 2025,Caribbean – Venezuela,1,6,,,Family says one missing was from Trinidad and Tobago[12][55]
6,16 October 2025,Caribbean,1,2,2,,Two survivors repatriated to Colombia and Ecuador[12][67]
7,17 October 2025,Caribbean,1,3,,,Allegedly affiliated with Colombian ELN[12][70]
8,21 October 2025,Pacific,1,2,,,First strike in Eastern Pacific; allegedly off Colombian coast[12][76]
9,22 October 2025,Pacific,1,3,,,[12][78]
10,24 October 2025,Caribbean – Venezuela,1,6,,,[12][59]
11–13,27 October 2025,Pacific,4,14,,1,Three strikes on four vessels leave one survivor; presumed dead[12][79]
14,29 October 2025,Pacific,1,4,,,[15][12]
15,1 November 2025,Caribbean,1,3,,,[12][73]
16,4 November 2025,Pacific,1,2,,,[12][83]
17,6 November 2025,Caribbean,1,3,,,[12][74]
18–19,9 November 2025,Pacific,2,6,,,Two vessels; three killed on each[84]
20,10 November 2025,Caribbean,1,4,,,[13]
21,15 November 2025,Pacific,1,3,,,First strike after formal unveiling of Joint Task Force Southern Spear[85][9]

## Methodology
For simplicity, we will define our area of interest (AOI) as the entire eastern Pacific-Caribbean area, from ... to .... We can take each date, and the day before and after, to compare VIIRS detections, looking for events that *do not* repeat. If needed, we can expand our temporal window. Then, we compare with what little locational data we can glean from other public sources to narrow our candidate detections. Save for that last step, most of this should be amenable to eventual automation, though I'd much prefer not needing to take it that far.

### Example
... 27 Oct ...

### Candidate Detections
In order to check a 1-day buffer, I checked VIIRS data from 31 August through 16 November. To include both the eastern Pacific and the Caribbean, we look at an AOI with a southwest corner of 6°S 120°W and a northeast corner of 33°N 50°W, which returns 383,133 detections. Filtering for events at sea using [Natural Earth](https://www.naturalearthdata.com/) 10-m land boundaries leaves 8,246 dectections. Conveniently, we only need to actually check known strikes and the days around them, which further reduces this to ...

Of these ... candidates, ...

### Evaluation and Discussions

## Comments and Feedback
I don't have a comments section on this page at the moment. Feedback can be submitted to the [Bluesky](link to post) post about this blog entry.
