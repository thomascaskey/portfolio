# portfolio
A portfolio of my work 📱

An interactive pixel-art Amsterdam canal at night. Open `index.html` in a browser:

- Each of the 8 canal houses opens a project card and has a shopfront for its app: RNZ record shop, 2degrees phone shop, TVNZ newsagent, Co-operative Bank, Drive Go house with a car in the garage, Sharesies exchange (after the Beurs van Berlage) and the Goodnotes school past the bridge.
- The houseboat is the professional About Me, the kiwi statue the personal one, and the clock tower has contact details.

Content lives in the data blocks near the top of `index.html`: `PORTFOLIO`, `CONTACT`, `PERSONAL` and `ABOUT`.

## Links

Every card has its own address: `/rnz`, `/2degrees`, `/tvnz`, `/co-operative-bank`, `/drive-go`, `/sharesies`, `/goodnotes`, `/coming-soon`, plus `/about`, `/personal` and `/contact`. Opening a link opens that card, and opening, switching or closing cards updates the address, so the back button works. On GitHub Pages, `404.html` sends a direct visit like `/portfolio/sharesies` back to the page. Opened as a local file, the page uses `#sharesies` instead.
