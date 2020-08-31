# To Do:

1. ~~Write proper README.~~
2. Projects Section
3. Papers Section

# Features

* Simple, easy to use, single page, A4-sized Resume generator.
* Print friendly, just use your browser or save as PDF.
* Write your resume in yaml. All content stored in data files.
* Configure sections from ```config.toml```.

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
* Contacts, useFontAwesome, dateUpdated pparameters in the config file are used in footer only, not in the resume itself.

# License

This project is open-sourced and licensed under the terms of the MIT license. I would be happy though, if you give attribution. <3