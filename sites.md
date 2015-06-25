---
title: Portfolio
permalink: /sites/
---

I am responsible for several different sites.  Here are links and a brief description of the site and my thought processes behind it.

This Site
---------

First, you are on my Github portfolio site.  This site is intended to be a quick site with information I find useful and links to projects that I have invested more time and effort into.  I have intentionally not made complex CSS or JavaScript on this site because it takes away from my efforts on other sites.  It is built with Jekyll.

Pack 198
--------

[Cub Scout Pack 198](http://vetsrights.com) is where I am currently putting most of my effort.  It is a live site I am building for my son's pack.  We do not currently have access to the domain, so it is live on a domain I have.  I will migrate it to the proper domain when I have access.

This site is completely hand coded evolving from a simple PHP e-commerce site built during courses at [Treehouse](http://teamtreehouse.com).  I use PHP extensively for site functionality.  The CSS is built using Sass and Compass.  

My next step for this site is to refactor it to the Slim micro framework and Twig for templating.  This will be a major project that I intend to use Git for progress tracking.

Once the refactoring is complete, I will add user registration, database functionality, a roster, photo upload, and group email functionality.  Then I will add additional JavaScript.  

This is the primary project site that I use to explore new techniques.  It was started with techniques taught in Treehouse courses but has evolved slowly since then.

Bible Word Study
----------------

[Bible Word Study](http://biblewordstudy.net) is a site I built with the Joomla CMS before I started any classes with [Treehouse](http://teamtreehouse.com).  It is very functional with Joomla plug-ins, but the styling is not what I would prefer.  Very little of this was hand coded.  It is focused on functionality instead.

Ralph Waldo Emerson
-------------------

The [Ralph Waldo Emerson](http://vetsrights.org) site is entirely from a course in Treehouse.  I coded this site along with the instructor in the course.  My server emulator (xampp on a Linux Mint os) did not handle the contact mail, so I put it live on another domain I control to test it.  This site was built with Slim and Twig and is the motivation for the Cub Scout refactor.  The simplicity of the build is refreshing, particularly the clean urls and DRY code.  The Cub Scout site primarily uses a clunky method of clean urls with subfolders and every page being called index.php.  Rewrite rules are also use to some extent, but the Slim framework provides a nice, streamlined method.

The one issue that I have found is that if you start with /index.php, Slim does not natively handle the redirects well.  I will have to add rewrite rules to handle that aspect of the site so it is not as fragile.

Other Projects
--------------

I previously built two sites for my prior business: sumnerlawpc.com and centerforvetrights.com.  Both sites were built with Joomla but are no longer live.  They had good functionality and were ultimately why I decided to leave the practice of law and start building web sites.  I can bring either live for a short time upon request.  It was more fun to build and tweak the sites than practice law.