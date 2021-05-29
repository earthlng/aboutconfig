## aboutconfig

The bare minimum to keep the old XUL-based `about:config` version available in Firefox 87+

Mostly copied from https://github.com/xiaoxiaoflood/firefox-scripts, all credit goes to them.


## Installation

1. download and extract the [master.zip](https://github.com/earthlng/aboutconfig/archive/main.zip)
2. copy the files/folders from `installdir` into your Firefox installation folder and the `chrome` folder from `profile` into your profile directory
3. load `about:support` and click the button "Clear startup cache..." (not sure if this is really necessary)
4. restart Firefox
5. you can now access the old `about:config` via `chrome://userchromejs/content/aboutconfig/config.xhtml`


### How it works

- `autoconfig.js` tells Firefox to load the autoconfig file `_autoconfig.cfg`
  - `_autoconfig.cfg` tells Firefox to look for (and load) `/chrome/utils/boot.jsm` in any profile running under this installation
    - `boot.jsm` instructs Firefox to load the `chrome.manifest`
      - `chrome.manifest` registers a `chrome://` namespace `userchromejs`
      
      
#### original files + modifications made

Mozilla removed the old `about:config` in https://hg.mozilla.org/mozilla-central/rev/2e2f7a1fd4fa

see the above link for the original files:

- toolkit/components/viewconfig/content/config.js
- toolkit/components/viewconfig/content/config.xhtml
- toolkit/locales/en-US/toolkit/about/aboutConfig.ftl
- toolkit/themes/shared/config.css

The only modifications are:
1. hardcoding all the localization stuff from aboutConfig.ftl into config.js and config.xhtml
2. remove the unnecessary telemetry stuff from config.js
