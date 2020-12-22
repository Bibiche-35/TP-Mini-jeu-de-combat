"# OCR-Concevez-votre-site-web-avec-PHP-et-MySQL" 
<H1>Pré-conception</H1>
Avant de nous attaquer au cœur du script, nous allons réfléchir à son organisation. De quoi aura-t-on besoin ? Une table 

//CREATE TABLE IF NOT EXISTS `personnages` (
//  `id` smallint(5) unsigned NOT NULL AUTO_INCREMENT,
//  `nom` varchar(50) COLLATE utf8_general_ci NOT NULL,
//  `degats` tinyint(3) unsigned NOT NULL DEFAULT '0',
//  PRIMARY KEY (`id`),
//  UNIQUE KEY `nom` (`nom`)
//) ENGINE=MyISAM DEFAULT CHARSET=utf8 COLLATE=utf8_general_ci;

<H1>Première étape : le personnage</H2>

<strong>code --> </strong>
//class Personnage
//{
//  private $_id,
//          $_degats,
//          $_nom;

<H2 Les fonctionnalités d'un personnage : </H2>

Un personnage doit pouvoir : 
Frapper un autre personnage ;

<strong>code --> </strong>
//  public function frapper(Personnage $perso)
//  {
    // Avant tout : vérifier qu'on ne se frappe pas soi-même.
    // Si c'est le cas, on stoppe tout en renvoyant une valeur signifiant que le personnage ciblé est le personnage qui attaque.

    // On indique au personnage frappé qu'il doit recevoir des dégâts.
  }

recevoir des dégâts.         

<strong>code --> </strong>
// public function recevoirDegats()
// {
    // On augmente de 5 les dégâts.
    
    // Si on a 100 de dégâts ou plus, la méthode renverra une valeur signifiant que le personnage a été tué.
    
    // Sinon, elle renverra une valeur signifiant que le personnage a bien été frappé.
// }
// }

Ensuite, à certains moments dans le code, il est dit que la méthode « renverra une valeur signifiant que le personnage a bien été frappé » par exemple. Qu'est-ce que cela peut bien signifier ? Ce genre de commentaire laissera place à des constantes de classe (si vous l'aviez deviné, bien joué !). Si vous regardez bien le code, vous verrez 3 commentaires de la sorte :

// Méthodefrapper(): « [...] renvoyant une valeur signifiant que le personnage ciblé est le personnage qui attaque » → la méthode renverra la valeur de la constanteCEST_MOI;

// MéthoderecevoirDegats(): « la méthode renverra une valeur signifiant que le personnage a été tué » → la méthode renverra la valeur de la constantePERSONNAGE_TUE;

// MéthoderecevoirDegats(): « elle renverra une valeur signifiant que le personnage a bien été frappé » → la méthode renverra la valeur de la constantePERSONNAGE_FRAPPE.

<strong>code --> </strong>
// const CEST_MOI = 1;
// const PERSONNAGE_TUE = 2;
// const PERSONNAGE_FRAPPE = 3;

<H1>Seconde étape : stockage en base de données</H1>

<H1>Troisième étape : utilisation des classes</H1>