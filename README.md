<!-- Writing conventions proposed by Andrew Wetmore, January 23, 2018 -->
# Apache Royale user documentation notes

## Audience
We have three main audiences:
1. Folks who have previously developed applications using Flex, and who want to learn whether and how to migrate their apps to Royale.
2. People who are new to AS and MXML, and possibly new to developing applications altogether, and want to know how to get started.
3. Experienced developers who want to see if Royale will give a better experience both in code development and through the application's lifecycle than what they have been using.

We can't assume that everybody understands the conversational shorthand Flex veterans use. Write for a person of good will who is reading to *find out*, and who wants to get to the next needed nugget of knowledge soon so they can go and make progress on the app they are working on. 

## Page structure
Each .md page starts with "front matter" structured like this:

```
---
# Licensed to the Apache Software Foundation (ASF) under one or more contributor license agreements.  See the NOTICE file distributed with this work for additional information regarding copyright ownership. The ASF licenses this file to You under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License.  You may obtain a copy of the License at
# 
# http://www.apache.org/licenses/LICENSE-2.0
# 
# Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
layout: docpage
title: README
---
```
Use HTML comments at the top of the document for any explanatory notes for the doc team (```<!-- Not finished yet - Andrew -->```) and for provenance when adapting existing material for Royale purposes (```<!-- Created by Peter Ent, modified by Tom Chiverton, as part of FlexJS documentation-->```).

## File names and titles
-  File names do not have to be the same as the titles that display at the top of the file.
-  For file names, use all lower-case, join words with - and not _ or ```%20``` statements, and add the markdown specification. The file name should be "another=important-thing.md", not "Another%20Important%20Thing.md", "AnotherImportantThing.md", or "Another_important_thing.md". This is important for SEO, human readability, and readability by assistive devices.
-  File titles should be in sentence case: "Another important Royale thing", not "Another Important Royale Thing". The point here is that the more capitals involved, the harder it is to read the statement.

## Documentation conventions
1. Address the reader directly, and in active voice, so "To do X, follow these steps..." rather than "When a developer wishes to do X, these steps would be followed..."
2. Instead of "he or she" use "they" when the pronoun is for an indefinite singular actor: "When someone has an existing application to migrate, they should start by..." This offends my grammarian soul, but is becoming standard English.
3. Link generously to other content in the help docs that may throw light on the current subject.
4. When writing how-to material, provide the *what*, the *so what*, and the *now what*: what a widget is, why widgets can be important in your code, and here's how to find, adapt, or create the widget of your dreams.

## Links

In the .md files, links have to be full paths without the leading slash. So to link to the published, HTML, version of /Welcome/Features/AS3.md, you would use

```[AS3](Welcome/Features/AS3.html)``` 

without the leading "/". Links are case-sensitive, and you need to insert ```%20``` for any space that appears in the target file's name. Check the guidance about file names, above.

When linking to locations not in the help-docs stack, including other pages in the Royale website, clicking the link should open a new browser window or tab so the reader does not lose their place in the help docs. MarkDown does not support the directive to open the link in a new window or tab, so use straight HTML for these links, like this:

```<a href="https://flex.apache.org" target="_blank">Apache Flex</a>```

## Build Locally

1. Install [Ruby+Devkit](https://rubyinstaller.org/downloads/). Ruby is required to run Jekyll.
2. Install [Jekyll](https://jekyllrb.com/).
3. If you want to provide a local configuration, copy `_config.yml` to `local_config.yml`.
4. To build the docs, run the following command:

    ```sh
    jekyll build --config local_config.yml
    ```
    The website will be rendered inside the `_site` folder.
5. To browse the docs using built-in Jekyll server, run the following command:
   ```sh
   jekyll serve
   ```
   The website will be available at `http://127.0.0.1:4000/royale-docs/`.
