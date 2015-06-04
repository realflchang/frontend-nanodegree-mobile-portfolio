Optimizations on main.js:

1. Replaced document.querySelector with document.getElementById or document.getElementsByClassName

2. determineDx is overly complicated and inefficient when the random pizzas reuse calculations on every 5th pizza. I have removed the determineDx function but done the following:
    a. kept the sizeSwitcher() function within the parent function (resizePizzas())
    b. newwidth calculation was revised so we do not have to access windowwidth (document.body.offsetWidth) everytime we access EACH random pizza. 

3. changePizzaSizes() function was rewritten so it does not call determineDx() and run thru all the recalculations. It first gets the windowwidth and newwidth before the FOR loop, and then apply the same width for every random pizza at once in the FOR loop.

4. Moved "var items" reference to mover class outside of updatePositions() function. We do not need to re-access the mover class everytime page is scrolled.

5. document.body.scrollTop does not need to be accessed within the FOR loop. I assigned it once outside the FOR loop into a variable called scrollTopVal.

6. In the updatePositions() FOR loop, the phase variable repeats its calculation on every 5th pizza. 
    a. I made the phase variable into an array
    b. I have revised the FOR loop so that for the first 5 in FOR loop, we proceed and calculate the phase value and store them into the array
    c. After the first 5, we simply reuse the phase value (in phase array) to cut down on recalculations
    d. mod calculation (i % 5) does not need to be recalculated everytime inside FOR loop. I have made it calculate once when the moving pizzas are being created and stored as a property value (elem.modVal)
    e. style.left triggers Layout and Paint, so I have replaced it with style.transform to position the pizzas
    
7. I only notice about 12 background pizzas at one time. I have reduced the number of sliding pizzas defined from 200 to 20.

8. Also both images pizza.png and pizzeria.jpg were optimized and reduced in sizes.

