---
title: Clustering setup
author: Sonia Hamilton
date: 2011-07-06
url: /2011/07/06/clustering-setup/
jabber_published:
  - 1309924321
categories:
  - Other-Tech
tags:
  - Clustering
  - Slug
---
A nice [post][1] from Jake on the SLUG list where he asks about a small clustering setup:

<p style="padding-left:30px;">
  I&#8217;m setting up some new hardware for a client of mine. Basically 2 new <a href="http://www.dell.com/au/business/p/poweredge-r210-2/pd">Dell PowerEdge R210 IIs</a> &#8211; nice and small and they seem quiet enough for an office (unlike the original R210). Anyway, quad core xeon, 2x 1Tb 7200RPM drives, 8gb ram (~$1500 each btw). The machines will be used as VM hosts (<a href="http://www.linux-kvm.org/page/Main_Page">kvm</a>) for a handfull of guests, file/domain server (<a href="http://www.zentyal.org/">ebox</a>), PBX (<a href="http://pbxinaflash.net/">piaf</a>), mail server web server, &#8220;magic windows only application&#8221; server etc. As the guests run everything in the ofice some kind of HA is needed.
</p>

<p style="padding-left:30px;">
  I&#8217;m thinking <a href="http://code.google.com/p/ganeti/">ganeti</a> is the way to manage it all as it takes care of <a href="http://www.drbd.org/">DRBD</a> and failover giving me a nice HA-ish setup without too much work.
</p>

<p style="padding-left:30px;">
  The questions. How should I setup my disks?
</p>

<p style="padding-left:30px;">
  I&#8217;m tossing up between, (all the below assume a small raid 1 partition for /, this is for the storage pool) RAID 1 with mdadm giving me 1 disk read speed but the ability to read 2 streams. RAID 1 with mdadm and fancyness giving me 2x read speed for a single stream, but normal behaviour for multiple streams and 1x write.
</p>

<p style="padding-left:30px;">
  RAID 0 with mdadm 2x read, 2x write and trust DRBD to look after my data ;->
</p>

<p style="padding-left:30px;">
  no RAID, set up as 2 separate drives use DRBD to look after data and get &#8220;more spindles&#8221; into the mix (so say file server lives on one disk and mail server on another)
</p>

<p style="padding-left:30px;">
  What deb based distro should I use for my host (or present a *really* compelling argument for something else)? I would use ubuntu as i&#8217;m most familiar with it but the recent debacle with unity has really hurt my confidence with them.
</p>

<p style="padding-left:30px;">
  Should i go to debian and if so which version?
</p>

<p style="padding-left:30px;">
  Networking<br /> each server has 2 gbit ports on it.<br /> should I<br /> team the nics, then run a vlan for drbd and another for regular coms<br /> dedicated nic for drbd and one for general coms.
</p>

<p style="padding-left:30px;">
  Any other suggestions or gotchas to look out for?
</p>

<p style="padding-left:30px;">
  I have my own answers to these questions, but I&#8217;d really like to hear any advice from the crowd (its like &#8220;the cloud&#8221; but open source and P2P ;->)
</p>

 [1]: http://lists.slug.org.au/archives/slug/2011/06/msg00014.html