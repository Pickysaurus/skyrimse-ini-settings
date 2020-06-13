# skyrimse-ini-settings
A JSON file containing all the Skyrim Special Edition INI settings and their descriptions. 

This is a community project, so please help me complete this by creating an issue or a Merge Request with updated information. 

Each setting should be formatted as follows:


``` typescript
export interface INIEntry {
    // @name: name of the INI entry (setting)
    name: string;
    // @title: alternate name to display e.g. ISizeH could be Horizontal Resolution
    title?: string; 
    // @section: which part of the INI did this appear in e.g. [General]
    section: string;
    // @description: human readable description of what this does. 
    description?: string;
    // @images: to use in the description/help modal. Left/Right compare and/or a single main image.
    images?: {
        compareLeft?: string;
        compaireRight?: string;
        main?: string;
    }
    // @type: what type of value is it (how should we render it?)
    type?: 'boolean' | 'string' | 'float' | 'number' | 'choice' | 'free-choice' | 'range' | 'special';
    value?: {
        // @current: the current value.
        current?: string | boolean | number;
        // @default: the default value used when the value is not assigned by the INI file
        default?: string | boolean | number;
        // @fixedDefault: the fixed default value (some default values are bugged and should never be used)
        fixedDefault?: string | boolean | number;
        // @max: the max value
        max?: number;
        // @min: the min value
        min?: number;
        // @low: the low preset value
        low?: string | boolean | number;
        // @medium: the medium preset value
        medium?: string | boolean | number;
        // @high: the high preset value
        high?: string | boolean | number;
        // @ultra: the ultra preset value
        ultra?: string | boolean | number;
        // @recommended: a recommended value
        recommended?: string | boolean | number;
    }
    // @choices: If "choice" or "free-choice" are chosen as the type, list the choices here.
    choices?: string[] | number[];
    // @rangeStepSize: If the type is 'range' this indicates which increments the slider moves in.
    rangeStepSize?: number;
    // @displayTab: Which tab should we load this into for Vortex's UI? If this is unfilled it will be classed as an "undocumented" value under "Advanced"
    displayTab?: string;
    // @category: For general the setting will be visible, for advanced it will appear under "advanced" in the displayTab, if not set, it will appear under "undocumented" in the displayTab. 
    category?: 'general' | 'advanced';
    // @allowPrefs: This setting works in the prefs INI
    allowPrefs?: boolean;
    // @hideIfBlank: Should this value not be printed to the resulting INI file if it's blank?
    hideIfBlank?: boolean;
}
```


Here is an example of a JSON entry for SIntroSequence
``` json
{
  "name": "SIntroSequence",
  "title": "Intro Video",
  "section" : "General",
  "type": "string",
  "value": {
    "default": "BGS_Logo.bik",
    "recommended": ""
  },
  "description": "The video to play on starting up the game. Must be the file name from the Data/Videos folder. Leave blank to skip the intro.",
  "displayTab": "General",
  "category": "general"
}
```
