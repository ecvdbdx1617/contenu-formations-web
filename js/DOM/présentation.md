# DOM

API pour manipuler un document HTML ou XML (arbre)


# Node

* n.children/childNodes
* n.parentNode
* parent.append(enfant)
* (anciennement) parent.appendChild(enfant)
* n.remove()
* n.replaceWith(n2)
    
Node.prototype.remove = Node.prototype.remove || function(){
    this.parentNode.removeChild(this);
}


# Document + HTMLDocument

* document.createElement('div')
    * créé une div orpheline

* document.querySelector(selector)
* document.querySelectorAll(selector)

Array.from(document.querySelectorAll('section h1')).map(...)


# Element + HTMLElement

* e.getAttribute(key)
    a.getAttribute('href')
* e.setAttribute(key, value)
* e.removeAttribute(key)
    * e.removeAttribute('hidden')

* e.textContent
    * e.textContent = ...

* e.id
* e.querySelector(selector)
* e.querySelectorAll(selector)
    * document.body.querySelectorAll()
    * var foot = document.querySelector('footer');
    foot.querySelector('.mentions-légales');
    
* /!\ e.innerHTML (getter/setter)
* e.insertAdjacentHTML(html, position)
* (moderne) e.classList (pour changer les styles)
    * e.classList.add/remove/has/toggle?
* (ancien, ne pas utiliser) e.className
<div class="yo hyz"></div>
    * .yo.hyz{}
    * .yo .hyz{}
    * .yo, .hyz{}

* e.style.backgroundColor
* maDiv.style.height = x+"%";

.yo{
    background-color: red;
}

* vider un élément
    * el.innerHTML = '';

# EventTarget

* n.addEventListener(type, listener)
```js
document.body.addEventListener('click', function(){
    console.log('yo');
})
```

* n.removeEventListener(type, listener)
    * Attention, comparaison par référence
    * var listener = function(){...}.bind(this);
    
* n.dispatchEvent(e)

* /!\ attributs on* interdits ! (onclick, etc.)
    * unique par élémént

# Evènements

* DOMContentLoaded
    * Quand le HTML est chargée et que l'arbre DOM est construit 
* load
    * Quand la page entière est chargée (CSS, fonts, images, etc.)
* click (mousedown/mouseup/dblclick)
* keypress (keyup/keydown)
* mouseover
* submit (&lt;form>)
* input
* change
* scroll

* "event delegation"

````js
el.addEventListener('click', function(e){
    // Event e
})
````

* e.target
* e.currentTarget
* e.preventDefault()
form.addEventListener('submit', function(e){
    e.preventDefault();
})

* e.stopPropagation()
* e.timeStamp


# Layout tree
