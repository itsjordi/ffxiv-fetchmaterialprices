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
4. It immediately asks [Universalis](https://universalis.app) what those
   ingredients currently sell for on the **Light** data center (hardcoded, not
   configurable) and works out a realistic price for however many you need —
   no second button, no extra click, it just happens.
5. It adds it all up. Anything that can't be sold on the market board gets
   labeled **Market prohibited** instead of a price, because the slave will
   not lie to you about gil it cannot conjure.

Prices aren't just "cheapest listing × quantity" — a listing is a whole lot
you can't split. If the cheapest one has 8 up for sale and you only need 3,
you're still buying (and paying for) all 8, and if that's still not enough,
the next-cheapest lot gets bought whole too. The slave spells out exactly
what got bought whenever that happens, instead of a flat unit price that
would understate the real cost. It also flags when the single cheapest
listing looks like a one-off fluke (a unit or two priced way under everything
else) so you don't mistake a lucky snipe for the real going rate. Elemental
crystals get split into their own section (still counted in the total,
just visually separate from real materials), and anything from a Treasure
Map gets flagged right in the ingredient table, since those tend to be a
much bigger ask than "go buy this."

You can also pin a home world (in the Light data center) and flip a switch to
only price what's actually sitting on your world — no pretending you'll
casually hop to another world just because it's 200g cheaper there.

That's the whole tool. There is no account system, no ads, no "premium tier,"
no Discord bot you need to invite to your server. Just a receipt.

## The tabs

- **Craft Cost** — type an item's name or paste its wiki URL, get the recipe
  and every ingredient priced automatically. Click any ingredient's name to
  see how it's actually obtained (gathered, bought, desynthed, retainer
  venture, Treasure Map, etc.), whether it's cheaper to craft it yourself, and
  an itemized breakdown when the price comes from more than one listing.
- **Item Lookup** — just checking how to get a specific material without
  pricing a whole recipe.
- **Shopping List** — combines everything currently sitting in your Basket
  into one consolidated buy list. If three different basket items all need
  Chondrite Ingot, this adds it up into one line instead of pricing (and
  buying) it three separate times.
- **Profit Calc** — type an item's name or wiki URL and the slave compares
  what the materials cost against what the finished item currently sells for,
  so you know if crafting it to flip is worth the trouble (includes a rough
  ~5% market board tax estimate).
- **Watchlist** — a saved list of individual ingredients you want to keep an
  eye on, independent of any recipe, with a "Recheck all prices" button, plus
  Export/Import so the list survives clearing cookies or moving browsers.
- **Glamour** — paste a glamour page link from
  [Eorzea Collection](https://ffxiv.eorzeacollection.com) and the slave finds
  every equipped piece, checks how each is obtained, and lets you jump
  straight into Craft Cost for anything that's actually craftable.

Hit "Add to basket" on anything you want made, then "Copy basket for Lycaa"
when you're done and paste it wherever Lycaa asked you to. Each search box
also keeps a "Recent" strip so you can click back into something you already
looked up, and most of them offer "Did you mean" suggestions (pulled straight
from the wiki's own search) if a typo comes up empty.

If a lookup fails, it's almost always the wiki's anti-bot defenses being
suspicious of a stranger asking it questions really fast — the log panel
shows exactly which fetch attempt failed and why, so it's not lying to you
about that either. Wait a few seconds and try again. Simple, already-obvious
problems (empty basket, no exact match, item's not craftable) get shown
directly instead of hidden behind "Technical details" — there's nothing
technical about "you didn't add anything yet."

## Known limitations (still accurate)

- It shows current listings at the moment you ask. Prices move. The slave is
  fast, not psychic.
- It only surfaces the immediate crafting ingredients (what the wiki page
  itself lists), plus one extra level for the "craft it yourself" comparison —
  it will not chase materials five tiers deep back to raw ore for you. That's
  a different, much more tired slave.
- The "fluke listing" and "lot-limited" detection are heuristics based on
  quantity and how far a price sits from the rest of the board — not a
  guarantee. Always sanity-check against the Universalis link before buying.
- The Glamour tab matches item names to the wiki automatically; if a name
  doesn't resolve cleanly, it'll say so and give you a manual wiki search
  link instead of guessing wrong.
- It relies on a public wiki, a public data API, and a public price API,
  routed through public CORS proxies because none of those sites particularly
  want to talk to a random webpage. If all of them are down at once, that's
  the internet's fault, not the slave's.
- Best hosted somewhere (GitHub Pages, etc.) rather than opened as a local
  file — some browsers refuse to let local files phone home, which is
  honestly a very reasonable thing for a browser to refuse.
- The basket, watchlist, home-world setting, and recent-searches lists live in
  your own browser's storage, not on a server anywhere — clearing your
  browser data clears them too (export the watchlist first if you care about
  it). The Shopping List tab only works for basket items added since this
  feature shipped (older entries won't have recipe data attached — just
  re-add them).

## Credits / not affiliated with anyone important

Data via Console Games Wiki, Garland Tools, and Universalis. Not affiliated
with Square Enix, Garland Tools, Universalis, or Lycaa. FINAL FANTASY XIV is
© SQUARE ENIX. This is a fan tool for people who would rather double-check
a price than log in and find out the hard way.
