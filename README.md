#### Email
- direct
- quantitative
- real-time
- A/B testing - feedback on design decision you make

#### Party like it's 1999
- email is like an invitation of the websites to party
- when person subscribes to receive emails they want to be in relationship with you
- 1-to-1 medium, not a blast tool

#### Iterate, test, iterate, test

### 5 rules
1. always send plain text alternative
2. design differently for email
3. test in different email clients
4. more copy, less images
5. listen to your readers

Utilitarian like text HTML emails
- forgot password
- receipt emails


Text emails look like they are coming from someone in the organization
- on-boarding - "reach out that everything is good with account"
- off-boarding - cancelation of account - "what can we do better? How we can improve a product?"

Wearables - plain text emails

#### Lots of emails suck especially on mobile
- links are broken
- don't render right
- unreadable
- text too small to read on mobile
- call to action button leads to a page that uses Flash - not accessible on mobile


Gmail cashes images
- some clients have images disabled
- tracking is not accurate

Bluehorn consumer survey
- 80% delete mobile email if it doesn't look good
- 30% un-subscribe!

### Strategy
1. Mobile First aka agnostic, aware, scalable
- considers mobile users a priority
- one layout for all screen sizes
- single column design 320-500px
- large text and buttons
- generous whitespace
- short and concise body copy
- usually leads to improved desktop design as well

2. Fluid
- email width changes to fit inside the window
- percentage based width
- text wraps automatically

3. Responsive
- display different context: "Try it now" vs. "Get the app and try it now"
- resize content, make images fit, make text larger
- hide content on mobile
- stack columns
- move a 2-column design to a 1-column design

### Email is NOT JPG, print ad or one-page site
| Email | Web |
| ------------- |:-------------:|
| `<table>` | `<div>` |
| `<td>` | `<h1>` |
| `<td>` | `<p>` |
| px | em |
| style="font-face" | `<style>` |
| bgcolor | background-color |
| padding | margin |

| Use this | Not this |
| ------------- |:-------------:|
| `#ffffff` | `#fff or rgb` |
| individual props | Shorthand |
| width="100" | width:100px |
| `<b>` | `<strong>` |
| align="left" | text-align: left |

### Why?
*Preprocessor*
- Sanitize "dangerous" HTML and CSS to protect the email client
- Remove object or embed tags, javascript, Flash, <style> blocks

*Gmail* - removes <style>
*Outlook* - multiple versions, uses explorer or MS Word to render, Mac outlook users have email rendered by Webkit

### Subscriber experience - best case scenario 30% open rate
1. From name
2. Subject line
3. Pre-header
4. Open
5. Tap/click
6. Page/Site

#### Container Table
- Reset default styles
- `table-layout:fixed` fixes yahoo alignment bug
`<table border="0" cellpadding="0" cellspacing="0" width="100%" style="table-layout: fixed;">`

#### Wrapper table
- hardcoded width 600 - Outlook doesn't handle well fluid containers
`<table border="0" cellpadding="0" cellspacing="0" width="600">`

#### Images are blocked?!
- provide alt text
- some browsers support styled alt text
- pair background colors for table cells

Blue border for linked images
Must use absolute path for images
A couple email browsers have issues with displaying https
Must constrain images
JPG, GIF, or PNG(not on lotus notes)

`<img src="img/abc.png" alt="ABC" width="100" border="0" style="display: block;" />`

All CSS should go inline
```
<td style="...">
<a style="...">
<img style="...">
<span style="...">
```
Margins are poorly supported

#### Hidden Pre-header text
```
<div style="display: none; font-size: 1px; color: #333333; line-height: 1px; font-family: Arial, sans-serif; max-height: 0px; max-width: 0px; opacity: 0; overflow: hidden; mso-hide: all;">
This won't be shown in design, but will be visible in the inbox preview
</div>
```
All styling should go within a cell

Set how alt text is being displayed
```
<img src="img/callout@2x" alt="Look at that full class" width="600" height="236" border="0"
style="display: block; padding: 0; color: #ffffff; font-family: Arial, sans-serif; font-weight: bold;
font-size: 24px; background-color: #f46e6c; -webkit-border-radius: 4px; border-radius: 4px;" />
```

#### Bulletproof buttons
- VML-based: MSFT proprietary language - use pre-built tool - https://buttons.cm/
- Padding based
- Border based

#### Web Fonts
- Google web Fonts
- Adobe Typekit
- Webfonts by Hoefler&Co
```
@font-face
@import
<link>

<td style="color: #333333; font-family: 'Proxima Nova', Helvetica, Arial, sans-serif; font-weight: normal; font-size: 18px; line-height: 22px">
```
Outlook does not support fonts, instead of a fallback displays Times New Roman
```
<!--[if mso]>
<style type="text/css">
  .body-text {
    font-family: Arial, sans-serif !important;
  }
</style>
<![endif]-->
```

#### Targeting email clients
```
<!--[if lt mso 12]>
<style type="text/css">
... Conditional CSS
</style>
<![endif]-->
```
| Year | Version |
| ------------- |:-------------:|
| Outlook 2000 | Version 9 |
| Outlook 2002 | Version 10 |
| Outlook 2003 | Version 11 |
| Outlook 2007 | Version 12 |
| Outlook 2010 | Version 14 |
| Outlook 2013 | Version 15 |

```
/* All of Webkit media query */
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  .display { display:block !important; }
}
/* Firefox Targeting */
@-moz-document url-prefix() {
  /** Insert styles here/
}
```
