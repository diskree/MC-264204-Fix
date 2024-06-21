## MC-264204 Fix

This is a server mod that fixes a bug due to which the death of a player from a goat is not tracked by advancements and is not taken into account in statistics.

This issue is tracked here: https://bugs.mojang.com/browse/MC-264204.

### Technical description

The damage dealt by the goat has a unique NO_ANGER flag, which hides the attacking entity from the attacked one, thereby preventing mobs from becoming aggressive in response to the attack. However, this flag does not account for cases where the attacked entity is a player. In such cases, it should not function this way, since players are not mobs.

The fix involves skipping the check for this flag when the attacked entity is a player, allowing the player to be aware of the attacking entity.

This hasn't been taken into account since they added the goat, but in Minecraft 1.20 it broke because Mojang did a refactoring and removed the code that was making it work more or less correctly.