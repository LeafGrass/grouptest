Real-Time Ousia
===============
&COPYRIGHT (C) LEAFGRASS;

&copy;
AT&T
"abcde"
&copy;
# This is an H1

## This is an H2

###### This is an H6

# This is an H1 #

## This is an H2 ##

### This is an H3 ######

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
> 
> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
> id sem consectetuer libero luctus adipiscing.

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
id sem consectetuer libero luctus adipiscing.

> This is the first level of quoting.
> 
> > This is nested blockquote.
> 
> Back to the first level.

> ## This is a header.
> 
> 1.   This is the first list item.
> 2.   This is the second list item.
> 
> Here's some example code:
> 
>     return shell_exec("echo $input | $markdown_script");

*   Red
*   Green
*   Blue


+   Red
+   Green
+   Blue


-   Red
-   Green
-   Blue


1.  Bird
2.  McHale
3.  Parish

3. Bird
1. McHale
8. Parish


*	Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
	Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
	viverra nec, fringilla in, laoreet vitae, risus.
*	Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
	Suspendisse id sem consectetuer libero luctus adipiscing.

*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
viverra nec, fringilla in, laoreet vitae, risus.
*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
Suspendisse id sem consectetuer libero luctus adipiscing.

1.  This is a list item with two paragraphs. Lorem ipsum dolor
	sit amet, consectetuer adipiscing elit. Aliquam hendrerit
	mi posuere lectus.

	Vestibulum enim wisi, viverra nec, fringilla in, laoreet
	vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
	sit amet velit.

2.  Suspendisse id sem consectetuer libero luctus
	adipiscing.

*   This is a list item with two paragraphs.

	This is the second paragraph in the list item. You're
only required to indent the first line. Lorem ipsum dolor
sit amet, consectetuer adipiscing elit.

*   Another item in the same list.

*   A list item with a blockquote:

	> This is a blockquote
	> inside a list item.

*   A list item with a code block:

        <code goes here>

1986. What a great season.

1986\. What a great season.

This is a normal paragraph:

    This is a code block.

Here is an example of AppleScript:

    tell application "Foo"
		beep
	end tell

    <div class="footer">
		&copy; 2004 Foo Corporation
	</div>

---

[Google]: http://google.com/

I get 10 times more traffic from [Google] [1] than from
[Yahoo] [2] or [MSN] [3].

[1]: http://google.com/        "Google"
[2]: http://search.yahoo.com/  "Yahoo Search"
[3]: http://search.msn.com/    "MSN Search"

*single asterisks*

_single underscores_

**double asterisks**

__double underscores__

un**frigging**believable

\*this text is surrounded by literal asterisks\*

Use the `printf()` function.

A single backtick in a code span: `` ` ``

A backtick-delimited string in a code span: `` `foo` ``

Please don't use any `<blink>` tags.

`&#8212;` is the decimal-encoded equivalent of `&mdash;`.

![Alt text](/path/to/img.jpg)

![Alt text](/path/to/img.jpg "Optional title")




Introduction
------------
"Ousia" is picked from Greek.
Mainly intend to represent the essence of Real-Time Theory.
Developed following K-I-S-S principle.


Source Tree Architecture
------------------------
core:
Ousia core routines. Ousia porting code are also placed here.
docs:
Complete documentation of Ousia.
driver:
Different kinds of device drivers based on Ousia.
They are all configurable.
framework:
Framework based on Ousia. Such as shell, vfs, etc.
They are scalable and configurable, either.
include:
Header files of main routines of Ousia.
platform:
Chip and board specific code, e.g. low-level library.
project:
Project source code. Include several sample project instances.
script:
Useful scripts used while Ousia developing.
support:
Basic supporting stuffs for Ousia developing and building.
Useful template files are placed here, such as porting code template.


Core Developing Steps
---------------------
-	Choose or create a branch to work on.
-	Update source code, include those version related strings.
-	Modify related makefile and config file.
-	Update Ousia Syscall Reference Document if necessary.
-	Update Ousia Release Notes if necessary.
-	Commit it.
-	Tag a new one if a new version commited.


Porting Steps
-------------
-	Create a directory named PLATFORM_NAME in folder "platform", then enter it.
-	Create three files: rules.mk config.mk target.mk.
	@rules.mk: makefile source code related rules
	@config.mk: parameters or flags for toolchains and environment
	@target.mk: rules for building target
-	Create a directory named "port" there then create three files in it.
	@ousia_cfg.h: os scalability related configuration.
	@ousia_port.h: header of porting code.
	@ousia_port.c: implentation of porting.
-	Create other porting related stuffs, such as linker scripts, if necessary.
-	Update TARGET_PLATFORM and PROJECT_NAME in main Makefile, then make.

Ps: If modify porting related code, should not edit directly in "core/port",
do that in specific platform directory instead, e.g. "platform/stm32/port".
Because makefile will copy them into "core/port" automatically.


Create User Project Steps
-------------------------
-	Create a directory named PROJECT_NAME in folder "project".
-	Add user source code.
-	Create a file rules.mk to specify source code related rules for makefile.
-	Update TARGET_PLATFORM and PROJECT_NAME in main Makefile, then make.
-	Ps: Refer to existing projects for further detailed information.


Build A Different Platform
--------------------------
Only modify the header TODO in root Makefile
-	Assign specific TARGET_PLATFORM and PROJECT_NAME


Download Code to Target Chip
----------------------------
-	Modify related User Customization Items in Makefile in source tree root.
-	Do proper Operation on hardware (i.e. change boot mode or reset or something).
-	Then type 'make install' is ok.

Ps: For stm32, there maybe a bootloader, 'make bootloader' will Download
bootloader code to chip via serial. And for x86, no code downloading procedure
is needed.


Acknowledgments
---------------
Parts of make system and libmaple stm32 low-level code are borrowed from libmaple.
Thanks to their excellent works! - http://leaflabs.com

