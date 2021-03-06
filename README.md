# PoliMorf
PoliMorf - WordPress theme with AWS compatibility

Design your sites without custom templates and store it on the Cloud.

Have you ever used a WordPress theme and felt restricted by the custom templates and options? Have you ever tried to change the style of elements but the theme didn’t let you do it? Have you ever got frustrated and thought about building your own theme from scratch instead?

If have experienced any of this then you are not alone. This was the whole reason I created PoliMorf, a WordPress theme that allows you to design and control what is on your site right down to the individual page and post level.  What makes PoliMorf different is that it only has a small amount of options even though it can do a lot. These options are simple text boxes where you add in a list of what should be on your page and on your site. It looks simple but behind it is powerful idea. 

PoliMorf works by creating a list of elements that looks partially like a static html page but without html tags. The theme uses a custom schematic language with its own syntax. For a page, there is no need to define a head, title or body. You define what is on the page within a standard “header, content, footer”-style of page layout. You can also define the whole page or part of the page, leaving the rest of the content to be what you write in WordPress. You can decide to only use WordPress content. The theme is compatible with that.

To change the architecture, you can also store your page “schematic” on AWS S3 and refer to it with a single command line in your page options, turning your WordPress database into a form of aggregator. The WordPress database has the basic elements of each page and post such as the title, excerpt and other meta-data like categories and author. But the content is pulled in from a secure place (your S3 bucket) and presented on the screen. So your database footprint gets reduced with the bulk of the data sitting on the Cloud. 

PoliMorf has filters that only allow certain formats to be processed, formats that you can control. So you can’t just pull in raw html and circumvent WordPress security practices. But you can use the filters to create html outputs easily. You can also decide to change all the command and syntax to a different language. Ever wanted to use Italian html attributes? You can with PoliMorf.

Since you can store most of your content on the Cloud, you can also develop your site in parallel. A local site can use the same references and pull the same content, or different content, from the same S3 account. So you can continuously develop your site without having downtime. 

PoliMorf balances the simple and the complex allowing you the freedom to leverage WordPress functionality. So you can use menus, widgets and even shortcodes if you wish. At the same time it allows you to build a site around a set of reusable data files that you can edit without changing your database footprint. 


# Features

- Individual control of content on each page and post - easily create different headers and footers, have a sidebar or not

- Ability to use WordPress functionality in conjunction with static content that you define.

- Beyond simple localisation - Allows the ability to change user language at attribute level

- Expandable function base - you can write your own custom functions

- Allows addition of extra stylesheet, script and font references in the header and footer by remote command. PoliMorf is compatible with other frameworks.

- Compatible with secure S3 buckets - incorporates public and private keys into the main settings

- Customizable settings using the WordPress Customizer.

- Fully responsive.

# Install

1. In your admin panel, go to Appearance -> Themes and click the 'Add New' button.
2. Click the 'Upload New' button.
3. Upload the zip file for PoliMorf that you downloaded
4. Click on the 'Activate' button to use your new theme right away.
5. Refer to the PoliMorf_User_Guide.pdf link on https://polimorfic.com/polimorf-theme/read-guide for how to customize this theme.
6. Navigate to Appearance > Customize in your admin panel and customize to taste.

If installing a newer version:

1. In your admin panel, go to Appearance -> Themes
2. Activate another theme
3. Delete PoliMorf
4. Add a new theme as above.

# Licence

PoliMorf WordPress Theme, Copyright 2018 PoliMorfic.com
PoliMorf is distributed under the terms of the GNU GPL as it is a
WordPress theme.

# 1. Basic Structure

PoliMorf creates custom page templates (not the mandatory WordPress ones) using lists of elements written in a schematic language. The language itself can be customised if required. The default schematic language is shown below.

In the Appearance->PoliMorf Settings page you add formats that apply site-wide. There are 7 formats:

- Header Format
- Footer Format
- Before Main Format
- After Main Format
- Post Format
- Page Format
- Sidebar Format

Combined together these make up a page/post format. The default page/post has Header, Main (either Post or Page Format) and Footer. The layout is full-width with no sidebar.

For example, a simple Post Format with WordPress content, comments and Previous/Next links would look like List A.
A simple Page Format with WordPress content and comments would look like List B.

List A

```
///HEADER:
%%DEFAULT::
///MAIN:
%%CONTENT_META::
%%CONTENT_DEFAULT::
%%PAGINATION::
%%COMMENTS::
///FOOTER:
%%DEFAULT::
```

List B

```
///HEADER:
%%DEFAULT::
///MAIN:
%%CONTENT_META::
%%CONTENT_DEFAULT::
%%COMMENTS::
///FOOTER:
%%DEFAULT::
```

The entries with "///" and ending in ":" are schematic tags. Entries starting with "%%" and ending in "::" are schematic commands. The identifiers (e.g. "///") can be customised to suit. 

# 1.1 Formats using theme options 

If you use the Theme Options, you don't need to use schematic tags for the elements. For the default post format you simply need to enter:

```
%%CONTENT_META::
%%CONTENT_DEFAULT::
%%PAGINATION::
%%COMMENTS::
```

For a default page:

```
%%CONTENT_META::
%%CONTENT_DEFAULT::
%%COMMENTS::
```

Any schematic tags will be removed when the options are saved. It also does not matter if you use spaces and new lines. This may help with readability.

If you add any data to the Before Main Format, After Main Format and Sidebar Format, the onscreen structure will change to include these elements. So, for example, full-width becomes main content with sidebar. You can override any global settings by using local formats with the custom meta field.

# 1.2 Formats using a custom meta field

Within each page and post there is a custom meta field for Format. In this you specify the complete page format including schematic tags. Taking List A again:

```
///HEADER:
%%DEFAULT::
///MAIN:
%%CONTENT_META::
%%CONTENT_DEFAULT::
%%PAGINATION::
%%COMMENTS::
///FOOTER:
%%DEFAULT::
```

The DEFAULT command refers to what is filled out in the Options. You can choose to enter other commands here detailing a specific header format if you wish. You can also link this to a file of schematic commands elsewhere.

