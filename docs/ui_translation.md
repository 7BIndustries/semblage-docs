# Translating the Semblage User Interface

This page is dedicated to information on translating the text within the Semblage user interface into additional languages.

## A Note on Translations

Many of the concepts in Semblage are technical in nature, and may be difficult to translate. The development team understands that it may not be possible to perform a direct translation of the original text. The translator may need to change the text significantly in order to effectively communicate the concept behind the subject. However, please keep line breaks and the sizing of user interface elements in mind while localizing the text. Symbols (icons) are used heavily in Semblage to help lessen the need to focus on user interface element sizing with different text in them. That is discussed next.

## Icon Symbology

Semblage makes heavy use of icons instead of text for buttons and UI elements, and the plan is eventually convert additional areas where there is text inside buttons currently to use icons. However, tooltips are still required for when the meaning of an icon is not obvious, and those need to be translated. The Godot game engine (that Semblage is built with) also supports the ability to change icons based on a locale. The symbols used in the icons have been chosen in an attempt to be as universal as possible, but if you feel that other symbols would work better, or a currently used symbol is not appropriate for your locale, please start a conversation on one of the community channels to discuss it.

## Adding an Additional Language

In the root directory of the Semblage project is a open document spreadsheet (ODS) file named `translations.ods`. This file should be opened in [LibreOffice](https://www.libreoffice.org/) (a free and open source spreadsheet program), as Microsoft Excel exports the end product (csv) file with some incompatible settings.

Once the spreadsheet is open, you will notice that the first column header is `keys`. These are the keys that are used to associate the translations with their matching user interface element(s). None of these keys should be changed. Each column to the right of `keys` holds the translations for an additional language, with the first being `en` (English). When adding a column header for a new language, be sure to use a valid locale code as described [here](https://docs.godotengine.org/en/stable/tutorials/i18n/locales.html#doc-locales) or Godot will not use the translations.

A matching translation/localization will need to be added for each English entry.

Once the translations are complete in the spreadsheet, save a copy of the spreadsheet in csv (comma delimited) format as this is the file that Godot will import and process. After that, it is time to submit the translations to the development team.

## Submitting Translations

A pull request can be opened on GitHub to request inclusion of your translations. This is the ideal route, but it is understood that some translators may not be comfortable with this process. You can also submit your spreadsheet to one of the community channels to have it considered for inclusion. However, please keep in mind that this workflow will make it harder to keep translations updated as Semblage grows and user interface text is added and corrected.

## Review

Translations will be reviewed to make sure they are accurate, appropriate, and do not contain any undesired text (i.e. spam).

## Testing Translations

It is currently fairly difficult to get set up to test translations. There are ways to make this process much easier, but they have not been implemented yet. If you are working on translations, please start a conversation on a community channel so the developers can prioritize allowing translations to be tested easily.

## Additional Resources

Below are links to Godot's translation documentation, which give additional information.

* [Internationalizing games](https://docs.godotengine.org/en/stable/tutorials/i18n/internationalizing_games.html)
* [Importing translations](https://docs.godotengine.org/en/stable/getting_started/workflow/assets/importing_translations.html)