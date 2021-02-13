# Features

* Simple, easy to use, single page, A4-sized Resume generator.
* Print friendly, just use your browser or save as PDF.
* Write your resume in yaml. All content stored in data files.
* Enable/Disable sections from ```config.toml```.
* Section names are configurable in ```config.toml```. So, you can write in any language you want.
* Change ```bib_style``` (APA, IEEE, else) for ```publications.yaml```.

# How To Use

## Download

1. Create a hugo project. 
2. Go to themes folder.
3. Clone this theme.

```
cd themes
$ git clone https://gitlab.com/mertbakir/resume-a4.git
```

## Start

1. Go to ```exampleSite``` and copy ```config.toml``` to the root directory of your hugo project. 
2. Open ```config.toml``` and add your relevant information.
3. Copy ```data``` folder from ```exampleSite``` to root directory. All you need is that folder.
4. Create your resume in yaml files.

## Notes

* Enable/Disable Sections in ```config.toml```
* Set avatar link in ```config.toml```, keep your image under ```static``` folder if you want.
* You can change bib_style in the config file. I've created options for APA and IEEE standards. You can configure ```publications.html``` file in the ```layouts\partials``` folder if you are looking for something else.
* [Here is the blog post](https://mertbakir.gitlab.io/projects/resume-a4/) about this project.

# License

This project is open-sourced and licensed under the terms of the MIT license. I would be happy though, if you give attribution. <3

> _I'm open to suggestions and contributions._

# My Work Flow

1. Make changes.
2. Delete resources folder in main project.
2. Build your hugo site using the theme. ```hugo server```
3. Copy "resources" folder from main project to theme folder ```themes\resume-A4\resources```
4. git commit & push.