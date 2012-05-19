-*- markdown -*-

django_haml is a template loader for Django 1.3 and 1.4 that allows you to use [HamlPy](https://github.com/jessemiller/HamlPy) in your templates.

It is based on the djaml project which is based on the [django-shpaml-template-loader project](http://bitbucket.org/jiaaro/django-shpaml-template-loader), and is licensed under the MIT license.

## Requirements

* [Django](http://www.djangoproject.org) -- Version 1.3 and 1.4 are known to work.
* [HamlPy](https://github.com/jessemiller/HamlPy)

## Installation

Use virtual environment and pip like a good lad would you?

        pip install django_haml

You can either copy all the files into 'djaml' in the root of your Django project
or install it using the included setup.py file.

Having done that, you need to add django_haml as the first item in TEMPLATE_LOADERS 
    
        TEMPLATE_LOADERS = (
                'django_haml.filesystem.Loader',
                'django_haml.app_directories.Loader',
            ...
        )

If you don't put django_haml first, then the standard Django template loaders will try and process
it first.

Make sure your templates have a .haml extension, and put them wherever you've told Django
to expect to find templates.

## Example

Here's a sample of what a Django layout file looks like using Haml:

        <!DOCTYPE html>
        %html
            %head
                %meta{'http-equiv': 'Content-Type', 'content': 'text/html; charset=UTF-8'}
                %title Internet Baseball League
                %link{'rel': 'stylesheet', 'type': 'text/css', 'href':'/site_media/css/grid.css'}
                %link{'rel': 'stylesheet', 'type': 'text/css', 'href':'/site_media/css/ibl.css'}
                %script{'src': "/site_media/js/modernizr-1.7.min.js"}
            %body
                %div{'class': 'row'}
                    #sidebar{'class': 'column grid_2'}
                        %img{'src': '/site_media/images/ibl_logo.gif', 'alt': 'IBL Logo'}<br>
                    #navcontainer
                        %ul#navlist
                            %li
                            %a{'href': '{% url home %}'} Home
                            %li
                            %a{'href': 'http://archive.ibl.org'} Archive
                            %li
                            %a{'href': 'http://iblgame.ibl.org'} Cards
                            %li
                            %a{'href': 'http://wiki.ibl.org/dokuwiki/doku.php?id=constitution'} Constitution
                            %li
                            %a{'href': '{% url free-agents %}'} Free Agents
                            %li
                            %a{'href': 'http://wiki.ibl.org/dokuwiki/doku.php?id=owners'} Owners
                            %li
                            %a{'href': '/results'} Results
                            %li
                            %a{'href': '/rotations'} Rotations
                            %li
                            %a{'href': '/schedule'} Schedule
                            %li
                            %a{'href': '/standings'} Standings
                            %li
                            %a{'href': '/starts'} Starts / Limits
                            %li
                            %a{'href': 'http://wiki.ibl.org'} Wiki
                            %li

                    #container{'class': 'column grid_10'}
                        {% block content %}
                        {% endblock %}


## The MIT License

Copyright (c) <2012> <Raymond Chandler III>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Shamelessly Stolen
This readme was shamelessly stolen from the djaml project.
