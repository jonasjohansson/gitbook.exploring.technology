# Colors

It is technically possible to go beyond Bitsy's limited palette by opening **game data** and editing the text. Any change to the editor gets immediately writing to the game data, and vice versa. Adding a color to a palette is easy:

1. Find the palette by looking for "PAL 0" where 0 is the number of the palette.
2. After the three rows of RGB values, add a fourth one with the desired values.
3. Find the object that should use the fourth color. The objects available are Tile \(TIL\), Sprite \(SPR\) and Item \(ITM\).
4. After the matrix of 0 and 1, add "COL 3". It's 3 because the Bitsy starts counting at 0!
5. Click anywhere outside of the game data window to trigger the change.

![](../../../../.gitbook/assets/roomgamedata.jpg)

