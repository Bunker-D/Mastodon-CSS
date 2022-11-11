
<a href="#how-to-use-those-files">
<img height="14px" src="https://upload.wikimedia.org/wikipedia/commons/a/a4/Flag_of_the_United_States.svg" alt=""  />
&nbsp;&nbsp;English</a><br>

<a href="#comment-utiliser-ces-fichiers">
 <img height="14px"  src="https://upload.wikimedia.org/wikipedia/commons/c/c3/Flag_of_France.svg" alt="" />
&nbsp;&nbsp;&nbsp;Français
</a><br>

<a href="#notes-to-developpers">
&nbsp;💻&nbsp;&nbsp;&nbsp;To developpers
</a><br><br>

![Demonstration](doc/mastodon.png)

---

# How to use those files

## Presentation

This is a CSS overlay that can be applied to the advanced web interface of Mastodon websites.<br>(Don't worry, you don't need to know CSS or what “CSS” even means.)

It brings:
- The ability to control the width of the columns (by dragging their lower right corner),
- A more rounded feel,
- The columns are spread rather than stacked to the left,
- The decorative image (bottom left) can be better handled in some instances, and the possibility to choose a custom one instead.

## Installation

### Set up the website and the browser to apply the custom theme

- If not already done, enable the avanced web interface for Mastodon, and the Dark theme\*:
  <br>Go in Mastodon “Preferences” (on the right side of the default Mastodon view). Then, in “Apparance”, check “Enable advanced web interface”, and select “Mastodon (Dark)” as the “Site them”.
  <br>\* Alternatively, if you do not want to use a dark theme, you can [remove the additional recoloring](#no-color) provided by this tool.
- Install the *Stylus* browser extension, or any other extension that allows to apply custom CSS to a web page. *Stylus* is available on [Firefox](https://addons.mozilla.org/en-US/firefox/addon/styl-us/) and [Chrome](https://chrome.google.com/webstore/detail/stylus/clngdbkpkpeebahjckkjfobafhncgmne)).
- Add a style for your Mastodon web page. Typically, for *Stylus*:
  - Go to the your Mastodon web page,
  - Click the button of the extension, then click “Write style for …”. (Stop at the first slash, thus including the name of your instance but not more than that.)
- Select [the right CSS file](#choose-the-right-css-file), copy-paste the CSS code in the *Stylus* window.
- [Customize](#customization) if need be.

### Choose the right CSS file

The only difference between the proposed CSS files lies in how the decorative bottom left image is handled. The optimal choice depends on what your Mastodon instance uses or what you want to use instead.

<!-- TODO choice diagram -->

- If you want to keep the **instance image**:
  - If your instance uses something that is integrated to the design **with transparancy**, and that shall be kept to the lower left corner (which is the Mastodon default with a mastodon drawing, seen in most instances), use [`mastodon.css`](mastodon.css).
  - If your instance uses a custom picture with **no transparancy** that should be properly framed and centered, use [`instance.css`](instance.css).
- If you want to use **you own image** (or **no image**):
  - If it has **transparancy** and be kept to the lower left corner, use [`custom-transp.css`](custom-transp.css).
  - If it has **no transparancy** and shall be properly framed, used [`custom.css`](custom.css).<br>
    (While `instance.css` will center the image when the column is too wide for it, `custom.css` was created to use higher resolution images that would take the whole available width, and be cropped accordingly to fit a target height.)

### Customization

#### Specify a custom picture

If you are using `custom.css` or `custom-transp.css`, find these lines (toward the end) and put the url of the image you want to use in between the parentheses:
```css
.drawer__inner__mastodon {
  background: url(""); /* 👈 Put image url here. */
```

With `custom.css`, by default, when the image is cropped, its center is kept. It might not perfectly fit your picture, but you can change that by modifying the next line:
```css
  background-position: center center;
```
The first `center` can be replaced with `top` or `bottom`, and the second `center` with `left` or `right`, depending on the area of the picture you want to keep.

#### Custom modifications

You can modify the rest of the code to your liking. For those unfamiliar with CSS, here are a few things you might want to do and how…

<details id="no-color"><summary><strong>Not happy with the new colors?</strong></summary><p>

Just remove the whole *Recolor* section (from `/* Recolor */` to `/* Roundness */`).

If just don't like the gradient on the leftmost column, remove this:
```css
.drawer__inner {
  background: linear-gradient(0deg, $left-bottom 0%, $left-top 100%);
}
```
For keeping a slightly darker color with no gradient, you can also replace it with:
```css
.drawer__inner {
  background: #333746;
}
```

</p></details>

<details><summary><strong>The bottom left image is too small or grows too big?</strong></summary><p>

Find these lines and change the maximal height (by default, `200px`) as you see fit:
```css
.drawer__inner__mastodon {
  max-height: 200px; /* 💡 If the bottom-left picture grows to big, change that. */
```

</p></details>

<br>

---

# Comment utiliser ces fichiers

## Présentation

Il s'agit d'une surcouche CSS qui peut être appliquée à l'interface web avancée des sites Mastodon.
(Ne vous en fait pas, vous n'avez pas besoin de connaître le CSS, ou même ce que “CSS” signifie.)

Ça vous apportera:
- La possibilité de contrôler la largeur des colonnes (en tirant le coin en bas à droite de chaque colonne),
- Un design plus rond,
- Des colonnes réparties sur la page web et non regroupées à gauche,
- Une meilleure prise en charge de l'image décorative (en bas à gauche) sur certains instances, et la possibilité de mettre la vôtre à la place.

## Installation

### Préparer le site et le navigateur pour appliquer le thème

- Si vous ne l'avez pas déjà fait, activez l'interface web avancée de Mastodon, et le thème sombre\* :
  <br>Cliquez sur “Préférences” (à droite dans la vue simple par défaut de Mastodon).
  <br>\*Alternativement, si vous ne voulez pas un thpme sombre, vous pourrez [retirer les couleurs](#pas-de-couleur) céées pas cet outil.
- Installez l'extension de navigateur *Stylus*, ou tout autre extension permettant d'appliquer un code CSS personnalisé à une page web. *Stylus* est disponible sur [Firefox](https://addons.mozilla.org/en-US/firefox/addon/styl-us/) et [Chrome](https://chrome.google.com/webstore/detail/stylus/clngdbkpkpeebahjckkjfobafhncgmne)).
- Ajoutez un style pour votre site Mastodon. Typiquement, avec *Stylus" :
  - Allez sur votre site Mastodon,
  - Cliquez le bouton de l'extension, puis cliquez sur “Write style for …”. (Arrêtez vous à la première barre oblique, incluant ainsi le nom de votre instance Mastodon mais pas plus que ça.)
- Sélectionnez [le bon fichier CSS](#choisir-le-bon-fichier-css), et copiez-collez le code dans la fenêtre ouverte par *Stylus* à l'étape précédente.
- [Personnalisez](#personnalisation) si nécessaire.

### Choisir le bon fichier CSS

La seule différence entre les fichiers CSS proposés est dans le traitement de l'image décorative en bas à gauche. Le choix optimal dépend de ce que votre instance Mastodon utilise, ou si vous voulez choisir votre propre image.

<!-- TODO choice diagram -->

- Si vous voulez garder l'**image de l'instance** :
  - Si l'image est intégrée au design du site avec de la **transparence**, et gagne à rester dans le coin en bas à gauche (ce qui est le cas de bien des instances, utilisant le dessin de mastodonte 🐘 par défaut), utilisez [`mastodon.css`](mastodon.css).
  - Si l'image est une image **sans transparence** qui gagne à être proprement cadrée et centrée, utilisez [`instance.css`](instance.css).
- Si vous voulez utilisez une **image de votre choix** (ou **pas d'image**) :
  - Si elle a de la transparence et gagne à rester dans le coin en bas à gauche, utilisez [`custom-transp.css`](custom-transp.css).
  - Si elle n'a pas de transparance, et doit gagne à être cadrée et centrée, utilisez [`custom.css`](custom.css).<br>
    (Tandis que `instance.css` centrera l'image quand la colonne de gauche est tros large pour elle, `custom.css` a été créé pour utiliser une image de plus grande résolution qui prendra toute la largeur disponible, et rognera pour atteindre la hauteur attendue. Typiquement, `piaille.css` a été créé pour piaille.fr, et remplace la photo d'oiseau de l'instance par une version de meilleure qualité.)

### Personnalisation

#### Choisir une image personnalisée

Si vous utilisez `custom.css` ou `custom-transp.css`, trouvez ces lignes (vers la fin), et mettez l'url de l'image que vous voulez utiliser entre les parenthèses :
```css
.drawer__inner__mastodon {
  background: url(""); /* 👈 Put image url here. */
```

Avec `custom.css`, par défaut, quand l'image est rognée, c'est son centre qui est gardé. Ce n'est peut-être pas le comportement idéal pour votre image, mais vous pouvez le changer en modifiant la ligne suivante :
```css
  background-position: center center;
```
Le premier `center` (centre) peut être remplacé avec `top` (haut) ou `bottom` (bas), et le second `center` par `left` (gauche) or `right` (droite), selon la zone de l'image que vous souhaitez garder.

#### Autres modifications personnelles

Vous pouvez modifier le reste du code comme vous le souhaitez. Pour ce ne maîtrisant pas le CSS, voilà quelques modifications que vous pourriez vouloir faire et comment :

<details id="pas-de-couleur"><summary><strong>Vou n'aimez pas les nouvelles couleurs?</strong></summary><p>

Retirez simplement toute la section *Recolor* dans le code (de `/* Recolor */` à `/* Roundness */`).

Si vous n'aimez juste pas le gradient dans la colonne de gauche, retirez :
```css
.drawer__inner {
  background: linear-gradient(0deg, $left-bottom 0%, $left-top 100%);
}
```
Pour toutefois garder une couleur légèrement plus sombre mais sans gradient, vous pouvez aussi remplacer ce code par :
```css
.drawer__inner {
  background: #333746;
}
```

</p></details>

<details><summary><strong>L'image en pas à gauche est trop petite ou devient trop grande ?</strong></summary><p>

Cherchez ces lignes et changez la hauteur maximale (`max-height`, qui est par défaut à 200 px) comme vous le souhaitez :
```css
.drawer__inner__mastodon {
  max-height: 200px; /* 💡 If the bottom-left picture grows to big, change that. */
```

</p></details>

<br>

---

# Notes to developpers

If you want to toy with this project, know that the CSS files are compiled from the SCSS files in the `sccs/` folder.
This allow to not have to manually duplicate the same pieces of code through the various CSS files.

The CSS might not be optimally organized: some selectors can appear several times.
This is because I prioritized ease of modification for the users (including those not knowing CSS).
Thus, the CSS is thematically organized (based on what it does), and a user can easily delete a whole section if they do not like what it does.
