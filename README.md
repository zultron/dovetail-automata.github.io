# Dovetail Automata LLC website

Written in Jekyll and hosted on GitHub pages


# Development

## Running in docker

    docker run -t -i --detach=false -v "$PWD:/src" -p 8080:4000 \
	    -u 1000 --name jekyll \
		grahamc/jekyll serve --watch --baseurl='' -V &

Then browse to http://localhost:8080/


## Installing the Alegreya-Sans-SC font locally

To edit the svg logos with text in Inkscape, the [fonts] need to be
installed locally.  Easiest is to put them into `~/.fonts`.

[fonts]: http://www.1001freefonts.com/d/5704/alegreya_sans_sc.zip


```
mkdir -p ~/.fonts
cd ~/.fonts
wget http://www.1001freefonts.com/d/5704/alegreya_sans_sc.zip
unzip alegreya_sans_sc.zip
# Maybe unnecessary
#mkfontscale .
#mkfontdir .
```


This font from:

```
@font-face {
  font-family: 'Alegreya Sans SC';
  font-style: normal;
  font-weight: 400;
  src: local('Alegreya Sans SC'), local('AlegreyaSansSC-Regular'), url(http://fonts.gstatic.com/s/alegreyasanssc/v3/6kgb6ZvOagoVIRZyl8XV-F1_68YLtTmKn7AnUVga1YU.ttf) format('truetype');
}
```

Cmd:
```
wget http://fonts.gstatic.com/s/alegreyasanssc/v3/6kgb6ZvOagoVIRZyl8XV-F1_68YLtTmKn7AnUVga1YU.ttf \
     -O fonts/AlegreyaSansSC.ttf
```
