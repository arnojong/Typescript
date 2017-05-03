# Canvas

Een Canvas is vergelijkbaar met een enkele afbeelding, waarvan je de pixels gaat manipuleren. De performance hiervan is veel beter dan het manipuleren van DOM elementen. Canvas leent zich daarom goed voor games met veel visuele effecten en animaties. Plaats een canvas element in de html pagina: `<canvas id="canvas" width="400" height="200"></canvas>`.

Je hebt een referentie naar de **rendering context** nodig om te kunnen tekenen. Die referentie haal je op via het canvas element:
```
let canvas : HTMLCanvasElement = <HTMLCanvasElement> document.getElementById('canvas');
let context : CanvasRenderingContext2D = canvas.getContext("2d");
```
Als je de context hebt kan je in de canvas gaan tekenen:
```
context.clearRect();
context.fillStyle = 'green';
context.fillRect(0,0,100,100);  
```

## Animatie

Voor animatie heb je een game loop nodig. Elk frame update je de coördinaten van je game elementen, en daarna teken je de hele canvas opnieuw. Bekijk [de broncode](./example.ts) om te zien hoe je meerdere canvas game elementen in een array kan plaatsen.

```
this.x = 0;
this.y = 0;
requestAnimationFrame(() => this.update());

private update():void {
    context.clearRect();
    
    this.x++;
    this.y++;

    context.fillRect(this.x, this.y, 100 ,100);  

    requestAnimationFrame(() => this.update());
}
```

## Spritesheets

Handgetekende of pre-rendered animaties kan je tonen met een spritesheet. Dit is vergelijkbaar met een .gif animatie, maar met hogere kwaliteit (een .gif heeft maar 256 kleuren). Je afbeelding bestaat uit een reeks frames:

![Sakura](../../docs/images/sakuraspritesheet.png "Sakura" =400x)

In je code moet je bijhouden hoeveel frames er zijn, hoe groot ze zijn, en welke op dit moment getoond moet worden.

![Sakura](../../docs/images/sakuragif.gif "Sakura")


## Links

- [Canvas API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
- [Canvas Drawing Tutorials](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial)
- [Canvas Animation](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_animations)
- [Spritesheets with Texture Atlas files](http://www.typescriptgames.com/TextureAtlas.html)