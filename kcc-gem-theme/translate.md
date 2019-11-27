# Google Translate

![Screenshot of WIOA's Google Translate button](../assets/img/translate_1.jpg)



![Screenshot of the language selection options in WIOA's Google Translate Menu](../assets/img/translate_2.jpg)



![Screenshot of the WIOA website translated into Korean](../assets/img/translated.jpg)


To enable Google Translate in a site, uncomment, or add, the following line in Jekyll's `_config.yml`:

```yaml
# _config.yml
translate: true
# More _config.yml
```



## The `.notranslate` Class

![Screenshot of WIOA's 'contacts' section translated to Korean showing each person's untranslated name.](../assets/img/notranslate.jpg)



Use the `.notranslate` class to prevent Google Translate from translating things like names and other proper nouns. For example, in the `_includes/contancts.html` file, the heading elements containing each contact's name have the class `.notranslate`. If you want to prevent translation of a proper known within a paragraph element (or another kind of element), simply wrap the word(s) in a `<span class="notranslate"><TEXT_NOT_TO_BE_TRANSLATED></span>` tag with the class.
