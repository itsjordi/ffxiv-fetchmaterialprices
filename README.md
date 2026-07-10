# Lycaa's Slave

*"the slave fetches; the slave does not explain itself."*

A single HTML page that does one (1) job: you give it a link to a craftable
item on the FFXIV wiki, and it tells you how many gil that item is going to
bleed out of you before it's even in your inventory.

It does not care about your glamour choices. It does not care that you only
need this for a relic step. It does not care that you already have 4 of the
5 mats sitting in your retainer and just forgot. It fetches prices. That is
its entire personality.

## What it actually does (the accurate part)

1. You paste a link like
   `https://ffxiv.consolegameswiki.com/wiki/AR-Caean_Velvet_Top_of_Striking`.
2. It scrapes that page just enough to find the item's ID.
3. It asks [Garland Tools](https://garlandtools.org) what the recipe is —
   ingredients and quantities, straight from the game data.
4. It asks [Universalis](https://universalis.app) what those ingredients
   currently sell for on whatever World or Data Center you tell it, and picks
   the cheapest listing for each.
5. It adds it all up. Anything that can't be sold on the market board gets
   labeled **Market prohibited** instead of a price, because the slave will
   not lie to you about gil it cannot conjure.

That's the whole tool. There is no account system, no ads, no "premium tier,"
no Discord bot you need to invite to your server. Just a receipt.

## How to use it

- Open the page.
- Paste the wiki URL of the item you want to craft.
- Click "Look up recipe."
- Type in your World or Data Center (e.g. `Twintania` or `Light`).
- Click "Get prices."
- Wince at the total.

If a lookup fails, it's almost always the wiki's anti-bot defenses being
suspicious of a stranger asking it questions really fast — the log panel
shows exactly which fetch attempt failed and why, so it's not lying to you
about that either. Wait a few seconds and try again.

## Known limitations (still accurate)

- It shows the cheapest **current** listing at the moment you ask. Prices
  move. The slave is fast, not psychic.
- It only surfaces the immediate crafting ingredients (what the wiki page
  itself lists) — it will not chase materials five tiers deep back to raw
  ore for you. That's a different, much more tired slave.
- It relies on a public wiki, a public data API, and a public price API,
  routed through public CORS proxies because none of those sites particularly
  want to talk to a random webpage. If all of them are down at once, that's
  the internet's fault, not the slave's.
- Best hosted somewhere (GitHub Pages, etc.) rather than opened as a local
  file — some browsers refuse to let local files phone home, which is
  honestly a very reasonable thing for a browser to refuse.

## Credits / not affiliated with anyone important

Data via Console Games Wiki, Garland Tools, and Universalis. Not affiliated
with Square Enix, Garland Tools, Universalis, or Lycaa. FINAL FANTASY XIV is
© SQUARE ENIX. This is a fan tool for people who would rather double-check
a price than log in and find out the hard way.
