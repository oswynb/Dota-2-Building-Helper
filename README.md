Dota-2-Building-Helper
======================

Building Helper Library for Dota 2 Modding

Author: Myll

**(1) BuildingHelper:AddBuildingToGrid(vPoint, nSize, vOwnersHero)**

Adds a new building to the custom grid given the target point, the size, and the owner's hero.

*vPoint*: The raw point where the user wants to place the building.

*nSize:* Length of 1 side of the building. Buildings must be square shaped. Example: nSize=2 would be 2x64 units. So, the building covers (2x64) by (2x64) units, or a total of 4 squares.

*vOwnersHero:* The hero which owns this building.

Returns -1 if a building can't be built at the location.

**(2) BuildingHelper:AddBuilding(building, vOwnersHero)**
Sub-functions of (2):

**RemoveBuilding(nSize, bKill)**
Removes this building from the custom grid.
*nSize:* The size of the building (see above).
*bKill:* Whether to ForceKill(false) the building or not.

**SetOwner(vOwner)**
Sets the owner of this building (a hero).

**GetOwner()**
Returns the owner of this building (a hero).

**UpdateHealth(fBuildTime)**
Update this building's health over the build time.

**SetFireEffect(bFireEffect)**
Whether this building should have a fire effect when its HP gets below 50%.

**GetFireEffect()**
Return whether this building should have a fire effect when its HP gets below 50%.

**(3) BuildingHelper:AddUnit(unit)**
Adds functionality to unit interactions with buildings.
Sub-functions of (3):

**GeneratePathingMap()**
Generates a pathing map for this unit. Primarily used to determine if a unit is interfering with building placement. Returns table full of center points of squares which the unit occupies.

**SetCustomRadius(nRadius)**
Sets a custom radius which will be used for determining the pathing map for a unit. Default is set to the unit's hull radius.

**GetCustomRadius()**
Returns the custom radius which will be used for determining the pathing map for a unit.

**(4) BuildingHelper:BlockGridNavSquares(nMapLength)**
Adds the squares blocked by the GridNav to the custom grid's blocked squares. This means buildings can't be placed on squares blocked by the GridNav. Not called by default.
nMapLength: The map's length on one side. Map must be square shaped.

Other functions:
**BuildingHelper:IsRectangularAreaBlocked(boundingRect)**
Returns whether this rectangular area contains a blocked square (bool).

**BuildingHelper:SetForceUnitsAway(bForceAway)**
Whether units should be forced away when a building is built on top of them. If false, buildings can not be built on top of units. Default is false.
Owners of buildings can always build buildings on top of themselves, and they are always forced away.

**snapToGrid64(coord)**
Snaps a coordinate to the 64-resolution grid.

**snapToGrid32(coord)**
Snaps a coordinate to the 32-resolution grid.

**makeBoundingRect(leftBorderX, rightBorderX, topBorderY, bottomBorderY)**
Quick way to define a bounding rectangle.

**tableContains(list, element)**
Return true if the table contains this element, returns false otherwise.
