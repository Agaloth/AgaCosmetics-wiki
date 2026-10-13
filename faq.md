# FAQ

**My hat or held cosmetic doesn't show on me.**
In creative mode your own hat and held cosmetics are not shown to you, because the creative client would turn
them into real items. Everyone else still sees them, and you get a one-time note in chat. For held items, the
cosmetic only shows while that hand is empty (`slot-options.offhand.require-empty`).

**I don't see my own backpack.**
Press F5. With a first-person model (`firstperson-item`), you see that model above your head instead of the
backpack.

**A cosmetic shows a barrier or nothing.**
Its item couldn't be made: the console says why at startup (for example "12 cosmetics use Nexo items, but Nexo
isn't installed"). Items from item plugins appear as soon as those plugins have loaded them.

**Bedrock players see nothing, or the model in the wrong place.**
Check [Bedrock](bedrock.md): GeyserDisplayEntity installed, the pack converted, the AgaCosmetics jar in Geyser's
`extensions/` folder, and a restart. Then fix positions with `/agac adjust` as a Bedrock player.

**Does it lag?**
Cosmetics are packets that ride the player; the server doesn't tick them. In a test with 50 moving players
wearing three cosmetics each, average tick time went from 9.8 ms to 11.5 ms.

**Can I use /reload or PlugMan?**
No. Replace the jar and restart (or use Paper's `plugins/update/` folder). Cosmetic, menu and wardrobe files
reload by themselves, so day-to-day changes need no reload at all.

**Spigot?**
No. AgaCosmetics needs Paper or Folia.

**Does /agac dataclear delete purchases?**
No. It clears what a player wears and their hidden states. Bought and given cosmetics and outfits stay; remove a cosmetic with
`/agac take`.

**Can HMCCosmetics and AgaCosmetics run together?**
Only while migrating. Both would draw cosmetics. Migrate, then remove HMCCosmetics.
