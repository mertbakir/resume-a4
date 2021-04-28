# !! Breaking Changes !!

Thanks to [@raphendyr](https://gitlab.com/raphendyr), we can now add more than one page and change order of the sections. Also, there are tons of refactoring which made the theme more modular.

**If you are already using a previous version of the theme, you will get an ERROR** after this update. Don't worry. The solution is very easy. You just need to edit ```projects.yaml```, ```features.yaml``` and ```config.yaml``` since their structure has changed. After that, all should be fine.

# Features

* Simple, easy to use, single or multi page, A4-sized Resume generator.
* Print friendly, just use your browser or save as PDF.
* Write your resume in yaml. All content stored in data files.
* Add/Remove sections order change section orders by editing `config.yaml`.
* Section names are configurable in `config.yaml`. So, you can write in any language you want.

[Here is a blog post](https://mertbakir.gitlab.io/projects/resume-a4/) about this project.

# How To Use

## Download

1. Create a hugo project.
2. Go to themes folder.
3. Clone this theme.

```
cd themes
git clone https://gitlab.com/mertbakir/resume-a4.git
```

or add as a submodule

```
git submodule add https://gitlab.com/mertbakir/resume-a4.git themes/resume-a4
```

## Start

1. Copy `config.yaml` from `exampleSite` to the root directory of your hugo project.
2. Open `config.yaml` and add your relevant information.
3. Copy `data` folder from `exampleSite` to the root directory of your hugo project. All you need is that folder.
4. Create your resume in yaml files.

## Config File

* You can add/remove sections.
* Add multiple pages as many as you like. (_still, let's not forget the aim here. a resume should be precise. I don't think a recruiter will scroll down on it._)
* Order of the "features" are important in the config file. 

### Custom CSS

Copy the ```\assets``` folder under the ```exampleSite``` directory if you like to make simple modifications.
### Avatar

Set avatar link in `config.yaml`, you may keep the image under `static` folder.
### Publications

You can change `style` of the `publications` feature in the config file. There are options for APA and IEEE standards. Report me on gitlab or send a merge requests if standarts are erroneous. I'm no expert on citation standarts.

# License

This project is open-sourced and licensed under the terms of the MIT license. I would be happy though, if you give attribution. <3

> _I'm open to suggestions and contributions._

# My Work Flow

1. Make changes.
2. Delete `resources` folder in main project.
2. Build your hugo site using the theme. `hugo server`
3. Copy `resources` folder from main project to theme folder `themes\resume-A4\resources`
4. `git commit` and `git push`.
