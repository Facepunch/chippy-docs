# Utilities

These are convenience functions that you can use inside of any scriptfunc.

??? example "Math"
    Function | Summary | Example
    :----------- |:------------- |:-------------
    `vec2` | create a vector with x & y components | `vec2(10f, playerPos.y)`
    `sin` | sine (returns from -1 to 1) | `sin(stageTime * 2f)`
    `cos` | cosine | `cos(bulletTime * 8f)`
    `fastSin` | not as expensive as `sin` and not as precise | `0.5f + cos(stageTime * 2f) * 0.5f`
    `sqrt` | square root | 
    `dot` | returns the dot product (useful to determine how similar two directions are) | `dot(playerFacingDir, playerGunDir)` returns -1 if the vectors are facing different directions, 1 if they are facing the same, etc
    `pow` | raises a number to the power of another number | `pow(radius, 2f)`
    `normalize` | gets the unit vector of a vector (length of 1) | `normalize(unitPos - playerPos)` 
    `dist` | finds the magnitude of a vector | `dist(playerPos - corePos)`
    `distSqr` | finds the square magnitude of a vector (less expensive) | `distSqr(playerPos - corePos)`
    `abs` | gets the absolute value (non-negative) | `abs(playerPos.x - unitPos.x)`
    `float` | converts an integer to a float (useful in division sometimes to prevent loss of precision) | `bulletNum / float(numBullets - 1)`
    `isNan` | returns whether a number is NaN (likely the result of a divide-by-zero) | `isNan(playerPos.x)`

??? abstract "Angles"
    Function | Summary | Example
    :----------- |:------------- |:-------------
    `angleToVec` | converts an angle (degrees) to a vector | `angleToVec(360f * (bulletNum / 5f))`
    `vecToAngle` | converts a vector to an angle | `vecToAngle(playerPos - bulletPos)`
    `angleBetween` | returns the closest angular distance between two angles | `angleBetween(playerFacingAngle, playerGunAngle)`
    `rotateAround` | rotates a point around an anchor: `rotateAround(pos, anchor, degrees)`. Leave out `anchor` to rotate around origin: `rotateAround(pos, degrees)`
    `rotateVec` | rotates a vector around the origin: `rotateVec(vec, degrees)`
    `perp` | gets a vector perpendicular to the input | `perp(facingDir)`
    `reflect` | reflects a vector across a normal vector | `reflect(dir, outOfBoundsNormal)` - will find the angle a bullet should bounce off the arena boundary
    `getRotationStrength` | determines how much a force would rotate an object: `getRotationStrength(hit position, force direction, pivot position, max distance expected)` | `getRotationStrength(hitPos, bullet.FacingDirection, unitPos, 20f)`
    `isLeftOfLine` | whether a point is to the "left" of a line: `isLeftOfLine(point, lineStart, lineEnd)`
    `projectPointOntoLine` | finds the nearest spot on a line to a certain point: `projectPointOntoLine(point, line0, line1)` | `projectPointOntoLine(playerPos, bulletPos, bulletPos + facingDir)`
    `doesLineIntersectCircle` | `doesLineIntersectCircle(line0, line1, circle position, circle radius)`

??? success "Rounding"
    Function | Summary | Example
    :----------- |:------------- |:-------------
    `round` | returns float rounded to the nearest whole number | `round(unitPos.x)`
    `floor` | rounds down to next whole number | `floor(unitPos.x)`
    `ceil` | rounds up to next whole number | `ceil(unitPos.x)`
    `roundToInt` | returns integer rounded to the nearest whole number | `roundToInt(unitPos.x)`
    `floorToInt` | rounds down to next whole number, returns integer | `floorToInt(unitPos.x)`
    `ceilToInt` | rounds up to next whole number, returns integer | `ceilToInt(unitPos.x)`
    `min` | returns smaller of two numbers | `min(patternNum, 2)`
    `max` | returns larger of two numbers | `max(roundToInt(damageDealt), 1f)`
    `truncate` | discards the decimal portion of a number | `truncate(-5.125f)` returns `-5f`
    `clamp` | clamps a value between a min and a max: `clamp(value, min, max)` | `clamp(patternPos.y, yMin + 5f, yMax - 5f)`
    `clamp01` | clamps a value between 0 and 1: `clamp(value)` | `clamp01(cloudFlashGlowPercent + 0.25f)`

??? failure "Rects"
    Function | Summary | Example
    :----------- |:------------- |:-------------
    `clamp` | clamps a position within a rect: `clamp(pos, rect)` | `clamp(playerPos, adjustRect(stageBounds, -5f))`
    `adjustRect` | modifies the bounds of a rect | `adjustRect(stageBounds, -5f)` or `adjustRect(stageBounds, vec2(10f, -5f))`
    `rect` | creates a rectangle: `rect(top left x, top left y, width, height)`
    `rectCenter` | creates a rectangle: `rect(vec2 centerPosition, vec2 size)`

??? todo "Easing"
    Function | Summary | Example
    :----------- |:------------- |:-------------
    `map` | maps a number from one range to another - `map(value, a, b, c, d)` returns a value from `c` to `d` based on how far along `value` is from `a` to `b` | `map(patternProgress, 0f, 1f, 1f, 10f)` (as patternProgress increases from 0 to 1, map returns a value from 1 to 10)
    `map` | map can also take an easing type | `map(distSqr(playerPos - bulletPos), 0f, 100f * 100f, 0f, 3f, 'QuadIn')`
    `mapReturn` | maps a number from one range to another and back again | `mapReturn(implodeProgress, 0f, 1f, 1f, 0.1f, 'QuadOut')` (as implodeProgress changes from 0f to 1f, return a value changing from 1f to 0.1f (halfway) then back to 1f)
    `ease` | ease toward a value | `ease(cloudFlashGlowPercent, 0f, 0.02f)` - returns a value 2% of the way from `cloudFlashGlowPercent` and `0f`
    `ease` | ease can be used with vectors as well | `ease(vectorVar, playerVel, 0.05f)`
    `getEasingType` | returns one of the 34 easing types (can be used for more variety) | `getEasingType(numShotPatternsConstant % 34)`

??? question "Strings"
    Function | Summary | Example
    :----------- |:------------- |:-------------
    `string` | converts a value to a text string | `string(dist(playerPos - (unitPos + unitFacingDir * -12f)))`
    `equals` | compares two strings to see if they are identical | `equals(bullet.DataPath, 'player/bullet/default')`
    `contains` | whether a string contains a substring | `contains(playerLastHitBullet, 'vine')`
    `concat` | merges strings together (can take either 2 or 3 strings) | `concat(myTauntString, '!!!')` or `concat('You destroyed ', myPixelDestroyVariable, ' pixels!')`

??? bug "Color"
    Function | Summary | Example
    :----------- |:------------- |:-------------
    `color` | creates a color | `color(1f, 0f, 0f) * 2f`, `color(1f, 1f, 0.1f, opacity)`
    `color255` | creates a color using 0-255 range rgb instead of 0-1 | `color255(140, 255, 244)`