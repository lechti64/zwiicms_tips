Ouverture du compte et paramétrage Snipcart

Ouvrir un compte chez SnipCart

https://app.snipcart.com/register

Valider le email de confirmation et remplir le formulaire

Ensuite vous ête redirigé vers le tableau de bord qui en en mode test.

Saisir les données d'identité pis cliquez sur votre profil

Dans Domain / Protocol indiquez https

Dans Regional Settings, régler la devise et le fuseau horaire et les pays dans lesquels vous vendez.

Dans Account / Api key sont listés les deux lignes à ajouter à votre CMS pour effectuer la liaison avec le panier. 

Paramétrage du CSM 

Dans Zwii, ouvrir le fichier /core/layout/main.css et coller entre <head> et </head> les deux dernières lignes étant donné que jquery est déjà inclus.

Ensuite remplacer la balise <head> par <<head lang=fr> afin d'afficher le panier en français.

Cliquez sur le messgae sous la forme d'un panneau d'avetissement, et sur validation, c'est le moyen de vérifier que votre installation est conforme. Tapez l'adresse de votre site et cliquer sur Check My Website.


Inclure les boutons d'achat. Ce bouton permet d'ajouter un objet dans le panier, il faut inclure ce code : 

<button
    class="snipcart-add-item"
    data-item-id="référence"
    data-item-name="Nom du produit"
    data-item-price="100.00"
    data-item-weight="dimension"
    data-item-url="/"
    data-item-description="Description du produit">
        Acheter
</button>

Inclure ce bouton sous un descriptif

Pour afficher le panier 

<a href="#" class="snipcart-checkout">Payer</a>

Pour lister le panier 

<div class="snipcart-summary">
    Number of items: <span class="snipcart-total-items"></span>
    Total price: <span class="snipcart-total-price"></span>
</div>


Lorsque un article est ajouté au panier, une fenêtre s'affiche en popup, pour l'empêcher ajouter ce script à la page :

<script
  type="text/javascript"
  id="snipcart"
  src="https://cdn.snipcart.com/scripts/snipcart.js"
  data-api-key="{API_KEY}"
  data-autopop="false"></script>

N'oubliez pas de remplacer evotre clé par celle indiquée sur le tableau de bord.

Création d'un template pour automatiser l'ajout d'un bouton :

Déposer le fichier snipcart.html dans /core/vendor/tinymce/templates
il contient ce code html :

<button
    class="snipcart-add-item"
    data-item-id="référence"
    data-item-name="Nom du produit"
    data-item-price="100.00"
    data-item-weight="dimension"
    data-item-url="/"
    data-item-description="Description du produit">
        Acheter
</button>


Ensuite modifier init.js

et ajouter

		{
            title: "Bouton Cartsnip",
            url: baseUrl + "core/vendor/tinymce/templates/snipcart.html",
            description: "Ajoute un bouton de paiement."
        }, 

dans la liste des Templates


Il ne reste plus qu'à passer le tableau de bord en mode live et engranger des commandes...


