# Jekyll Website
#### TOC
1. [Basics](#1)
2. [General Info](#2)
3. [How it Works](#3)
4. [The Blog](#4)
5. [The Old Site](#5)
----

## 1. Basics:<a name="1"/>
* This website is built using the jekyll server on your computer.
* The jekyll server will regenerate the statice site in the `site` folder each time you save the file.
* There is no need to run jekyll on the server.  *static*

----

## 2. General Info:<a name="2"/>
* To clone the repo:
`git clone https://github.com/uscvkp/website.git`
* To edit the site locally:
`sudo jekyll serve`
* To build and upload the site:
```
$ sudo jekyll build
$ git add -A
$ git commit -m "I did something.  I'm important"
$ git push
```
* To deploy the site:
  - Log on to the production server
  - Enter the following terminal commands:
```bash
$ sudo -i
$ cd /var/www/jekyll
$ git pull
$ cd ..
$ rm -rf html.bak
$ mv html html.bak
$ mkdir html
$ cp -rf ./jekyll/_site/* ./html
```
----

## 3. How it works:<a name="3"/>
### Code vs. Data -- liquid templates
* The code is separated from the content
  - This way the content can be acted upon in a `for-loop`
  - This makes it easy to format the data differently
* Here are excepts from two files that should help you understand the concept
  - Take note of the directories and file names
  - The directories and file names for the other pages will match up accordingly
  - The html should be short, but the data could be close to 300 lines in some cases

**/_my_pages/talks.html**
```django
{% for t in site.data.talks %}
  {% if t.older != true %}
    <p>
      {{t.title}}
      <br>
      Download :
      <a href="/assets/talks/{{t.link}}" title="Download document">
        <img style="position:relative; top: 2px;"
             src="/images/ppt_icon.gif"
             alt="Ppt document" />
        [ppt]
      </a>
    </p>
  {% endif %}
{% endfor %}
```

**/_data/talks.yml**
```
- title : High-Level Synthesis of Genomic Search Engine, Dec. 2, 2016&#58;  ReConFig 2016
  link  : reconfig16_talk.pptx

- title : 4 Minute Madness, Nov. 18, 2016&#58;  Heterogeneous and Reconfigurable Computing Group
  link  : 1minutemadness16.pptx
```
----

### Jekyll uses SASS
`$grey-color:       #828282;`
* SASS uses variables, but CSS does not.
* The SASS is compiled by the Jekyll server as you are editing the site.
* CSS is cascading: order is important because your values can be overwritten.
* The main SASS file is in the CSS folder.  
* Take note of the import statements and their order.
* This should tell you that the best place to add a new style would be the my-styles.scss

```css
@import
        "base",
        "layout",
        "syntax-highlighting",
        "my-styles"
;
```
## 4. The Blog<a name="4"/>
* The Blog is Jekylls highlighted feature
* It has markdown support _as the other pages do_
  * I'm not sure how well the markdown will work within a lucid templates
* People choose it because it's hosted on github pages for free
* Jekylls initial setup page had a blog for you, but I wasn't sure where or if you wanted it
* If you would like to try it, you can type the yoursite/blog in the address bar
* Jekyll ships with a blog post that tells you how to use the blog
* I copied and pasted this blog post to test the blog
* Now you have two blog tutorials.  No extra charge!


## 5. The Old (currently hosted) Site<a name="5"/>
* You should know that there are some problems with the other site
* There are colors defined as 10 numbers and other things
* The pages don't really show any text in firefox, but it works in chrome
* I'm pretty sure that Android uses the firefox build engine though.  Linux
* The other menu didn't have an active class, but the one installed on this site is just copied from the bootstrap website








