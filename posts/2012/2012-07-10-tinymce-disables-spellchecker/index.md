---
title: "TinyMCE Disables Spellchecker"
date: 2012-07-10
categories: 
  - "writing"
tags: 
  - "drupal"
  - "web-development"
---

**Problem**: TinyMCE rich-text editor disables the operating system spellchecker when using Firefox or Chrome.

**Solution**: Set the TinyMCE configuration "gecko\_spellcheck" to TRUE.

```
tinyMCE.init({
	...
	gecko_spellcheck : true
});
```

In Drupal, you can override this setting by adding an alter function to a custom module.

```
function MYMODULE_wysiwyg_editor_settings_alter(&$settings, $context) {
  if ($context['profile']->editor == 'tinymce') {
    $settings['gecko_spellcheck'] = TRUE;
  }
}
```

Source: http://drupal.org/node/1064268
