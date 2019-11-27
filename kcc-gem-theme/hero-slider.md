# Hero Slider Component

## Overview

![The hero-slider on the Foundation website](../assets/img/hero-slider.jpg)
{: style="height: auto; width: 100%: max-width: 100%" }

The hero-slider component consists of an `_includes/hero-slider.html` file, a `slider.js` file, `_hero-slider.scss`, and the page you want the slider to appear in. You also need to define a `slides:` collection in the page's YAML front-matter.

```
 ./
  |-- _includes/
  |     |__ hero-slider.md // File to include via Liquid
  |
  |--assets/
  |     |__ js/
  |     |    |__ theme/
  |     |           |__ src/
  |     |                 |-- wrapPowerText.js // Wrap **TEXT** in a stylized span
  |     |                 |__ sliders.js // Custom JS/slick for functionality
  |     |__ scss/
  |          |__ 2-modules/
  |                 |__ _hero-slider.scss // Styling rules
  |
  |__ index.html // File to house the slider. Usually the homepage.
```



---

## Usage

### In-page `slides` collection

First, in the page you have chosen the slider to appear in, define the slides collection using the `slides:` key in the file's front-matter.  Each slide should contain all the front-matter fields shown below.

If the slide's image has a white colored background, it should get an extra front-matter key and value of  `white_background: true` .

```yaml
slides:
  - image: uploads/<IMAGE_NAME>.jpg
    alt-text: "Alternate text for the slide's img element"
    url: "URL for slide's link (must use protocol)"
    text: Heading to appear over the slide. (OPTIONAL) If the image has text already, you may want to leave this value blank.
  # white_background: true ## (OPTIONAL) Add for images with white colored backgrounds
```

#### Image

**ALL SLIDES MUST BE CROPPED TO A 16:9 WIDTH:HEIGHT IMAGE RATIO**

The `image: ` key's value should contain the path to the image for the slide

#### Alt-text

The alt-text that appears in the slide image element's alt tag. This alt-text is required for web-accessibility. **If the slide-image contains readable text that is not strictly decorative, type the text into the `alt-text:` field.**

#### URL

The `url:` key's entry can be one of the following:
- Absolute url's containing the protocol (**note: you should _only_ use absolute links for sites at a different domain or sub-domain**):
  - e.g. `https://foundation.kcc.edu/give` or `http://www.kcc.edu/`
- Root relative url's or relative url's with directory traversal (**note: relative url's should never have the domain i.e. do NOT use: 'foundation.kcc.edu/give'**):
  - Root relative: `/give` | with directory traversal: `../give` (**note: sliders/image-carousels are usually on the homepage, so the 'with directory traversal' usage case is rare**)
- Relative url with no baseurl/directory traversal/domain:
  - e.g. `give`

KCC's policy is to open external links (links residing on a different domain than the user's location) in a new tab. Since absolute links are jumping to another domain, absolute url's get the addition of the `target="_blank"` attribute/value pair.

##### How is the type of URL determined?

The Liquid forloop in `_includes/hero-slider.html` that iterates over the slides, checks slides url's for absolute and relative links:
1. If the url contains a protocol (`https://` or `http://`) it uses the literal value for `{{ slide.url }}` in the `href` attribute and adds `target="_blank"`.
2. If the first character of the url is a `.` or `/` (the url has directory traversal or an absolute path) it also uses the literal value for `{{ slide.url }}` in the `href` attribute but does NOT open in a new tab.
3. Everything else is regarded as a relative url with no baseurl/directory traversal/domain and get's the `{{ slide.url }}` prepended with `{{ page.baseurl }}` (i.e. `href="{{ page.baseurl }}{{ slide.url }}"`).

#### Text

`text: ` is the contents of the heading that will appear in front of the slide-image. Use a short/concise phrase or sentence for its value—long `text: ` entries will cause layout issues.

If your image already contains text, you can omit the heading by leaving `text:`'s value blank. **The text key's VALUE is optional, however, its key is required.**

##### "The POWER of Community" text-effect

You can easily wrap a word in a `<span>` tag that applies styling to make the text more bold.  Use double-asterisks on either side of a word      ( e.g. `**<TEXT>**`). **DO NOT INCLUDE WHITESPACE ANY WHITESPACE CHARACTERS IN BETWEEN THE DOUBLE_ASTERISKS INCLUDING WORDS SEPARATED BY SPACES**

the `assets/js/theme/src/wrapPowerText.js` module handles the functionality for this text-effect.

#### (OPTIONAL) `white_background:` Key

If the slide-image has a white background, add the optional `white_background: true` setting to the slide. This applies a class to that slide to provide a subtle light gray border for visual contrast against the page's background.

#### Example Slides Collection

Below is a copy of the `slides` collection  from  the foundation homepage's front-matter:

```yaml
slides:
  - image: uploads/scholarships-open_superhero-banner.png
    alt-text: "The Scholarship application is now open. Application is open November 1 to March 1 for Fall 2020. Apply one time to be considered for all available scholarships at foundation.kcc.edu/scholarships. $200,000 in scholarships is awarded annually."
    url: /scholarships
    text:
    white_background: true
  - image: uploads/super-power.png
    alt-text: What's your super power?
    url: /scholarships/recipients-donors
    text:
  - image: uploads/dr-boyd.png
    alt-text: The Power of Community
    url: 'https://foundation.kcc.edu'
    text: The **POWER** of Community
  - image: uploads/students_on_back_patio_oct2015_D41_0619-web.jpg
    alt-text: The Power of Education
    url: 'https://foundation.kcc.edu'
    text: The **POWER** of Education
  - image: uploads/2017_graduates_KCC_066.jpg
    alt-text: The Power of Giving
    url: 'https://foundation.kcc.edu'
    text: The **POWER** of Giving
```



### Include the `hero-slider.html` File

The includes file contains the html template to build-out the slider's elements. It utilizes lazy-loading on all slides except the first. It contains a Liquid forloop that iterates over the page's slide collection to create a slide for each item. The slides will be in the order that they appear in the page's front-matter YAML settings.

`_includes/hero-slider.html` already contains Bootstrap 4 `row` and `col` elements. The Liquid include statement should appear as a child of an element with the Bootstrap 4 `.container` class.

```html
<section class="position__offset-fixed-nav">
  <div class="container container--tan-bg">
    {% includes hero-slider.html %}
    <!-- More page content below
    ... -->
  </div>
</section>
```



### Adjust the `.hero-slider__slider--heading-container` width

Depending on how many slides are in the slider, the its headings may appear off-center. You may need to override the `kcc-gem-theme`'s styling rules for the `.hero-slider__slider--heading-container` class to recenter them. This is usually only a couple percentage difference (`2%`).

To override the gem theme's styling, add the following rules to your current projects SASS files. The link to the `kcc-theme.css` stylesheet appears higher in the page's HTML than the project's `main.css` stylesheet. As a result, any duplicate selector's and rules in the project's stylesheet will override the gem theme's

```scss
// In `assets/scss/2-modules/_hero-slider.scss (Don't forget to @import)
.hero-slider__slider--heading-container {
  width: 10%;
}
```



---

## Files

### `hero-slider.html` Includes-File

```html
<div class="row">
  <div class="col hero-slider__slider">
  {% for slide in page.slides %}
    {% if forloop.first == true %}
    <div>
      <a {% if slide.url contains 'https://' or slide.url contains 'http:// %}target="_blank" href="{{ slide.url }}"{% elsif url_first_char == '.' or url_first_char == '/' %}href="{{ slide.url }}"{% else %}href="{{ page.baseurl }}{{ slide.url }}{% endif %}"><img src="{{page.baseurl}}{{slide.image}}" class="img-fluid hero-slider__slider--slide-img {% if slide.white_background %} hero-slider__slide-img--border{% endif %}" alt="{{slide.alt-text}}" /></a>
      <div class="hero-slider__slider--heading-container text-center">
        <h3 class="hero-slider__slider--slide-heading">{{slide.text}}</h3>
      </div>
    </div>
    {% else %}
    <div>
      <a {% if slide.url contains 'https://' or slide.url contains 'http:// %}target="_blank" href="{{ slide.url }}"{% elsif url_first_char == '.' or url_first_char == '/' %}href="{{ slide.url }}"{% else %}href="{{ page.baseurl }}{{ slide.url }}{% endif %}"><img src="assets/img/placeholder.png" data-src="{{page.baseurl}}{{slide.image}}" class="img-fluid hero-slider__slider--slide-img {% if slide.white_background %} hero-slider__slide-img--border{% endif %}" alt="{{slide.alt-text}}" /></a>
      <div class="hero-slider__slider--heading-container text-center">
        <h3 class="hero-slider__slider--slide-heading">{{slide.text}}</h3>
      </div>
    </div>
    {% endif %}
  {% endfor %}
  </div>
</div>
```



### `wrapPowerText.js` File

The `assets/js/theme/src/wrapPowerText.js` file contains vanilla JS for wrapping slide-text in a stylized span if it uses the proper syntax.

With this custom JS, the slide text `The **POWER** of Community` will render as `The <span class="typography__power-text">POWER</span> of Community`.

```javascript
const SLIDE_HEADING_ELEMENTS = document.querySelectorAll('.hero-slider__slider--slide-heading'); // Element from HTML
const regEx = /\*\*(\S+)\*\*/g;
const replacement = '<span class="typography__power-text">$1</span>';

function replaceRegex(el) {
  return el.innerHTML = el.innerHTML.replace(regEx, replacement);
}

function loopOverNodeList(nodeList) {
  for (var i = 0; i < nodeList.length; i++) {
    replaceRegex(nodeList[i]);
  }
}

function wrapPowerText() {
  if ( !document.querySelectorAll('.hero-slider__slider--slide-heading') )
    return; // Bail out of theres no slider in the page.
  loopOverNodeList(SLIDE_HEADING_ELEMENTS);
}

export default wrapPowerText;

```



### `sliders.js` File

The `assets/js/theme/src/sliders.js` file contains a module with custom JS/jQuery for the slick-slider functionality. **Slick requires jQuery to work.**

See <https://kenwheeler.github.io/slick/> for detailed documentation on the Slick slider.

Each custom slick setting is commented in the JS below:

```javascript
function initSliders() {
  function initSlick() {
    $('.hero-slider__slider').slick({ // Settings Object specific to slick.js // https://kenwheeler.github.io/slick/
      dots: true,  // Show slide indicator dots. 1 dot per slide appears at the bottom.
      slidesToShow: 1, // How many slides are shown at a time
      slidesToScroll: 1, // How many slides to change when navigating through them
      autoplay: true, // Start rotating the slides ASAP
      autoplaySpeed: 3000, // Amount of time in miliseconds that each slide is displayed
      prevArrow:'<img alt="Previous slide" class="a-left control-c prev slick-prev" src="/assets/img/dbl-prev.svg">', // Custom HTML to inject for the previous-slide icon/button.
      nextArrow:'<img alt="Next slide" class="a-right control-c next slick-next" src="/assets/img/dbl-next.svg">' // Custom HTML to inject for the next-slide icon/button.
    });
  }
  document.querySelector('.hero-slider__slider') ? initSlick() : null; // If the page has a slider run `initSlick()`, otherwise bail-out!
}
export default initSliders;
//  USAGE:
//    import initSlick from './sliders.js'; // Import the default function at the top of your JS file
//
//    document.addEventListener('DOMContentLoaded', function() {
//      initSlick(); // Fire the function after the DOM has loaded.
//    });
```
