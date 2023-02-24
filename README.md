# sfcc-sfra-vs-code-snippets
Salesforce Commerce Cloud SFRA VS Code Snippets

This snippet can be added to VS Code and with the shortcut prefixes , you can add code blocks and swiftly do development on SFRA projects in SFCC.

-- First Snippet is Adding Logger --- 
ShortCut: sfcclog  
Code: dw.system.Logger.getLogger('custom', 'custom').error('$1' + JSON.stringify($2));  


-- First Snippet is Adding Logger --- 
ShortCut: sfccsite  
Code: 
`var Site = require('dw/system/Site');
  var $1 = Site.current.getCustomPreferenceValue(''); `
  
  
