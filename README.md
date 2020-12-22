"# OCR-Concevez-votre-site-web-avec-PHP-et-MySQL" 
<H1>Pré-conception</H1>
Avant de nous attaquer au cœur du script, nous allons réfléchir à son organisation. De quoi aura-t-on besoin ? Une table 

<!-- CREATE TABLE IF NOT EXISTS `personnages` (
  `id` smallint(5) unsigned NOT NULL AUTO_INCREMENT,
  `nom` varchar(50) COLLATE utf8_general_ci NOT NULL,
  `degats` tinyint(3) unsigned NOT NULL DEFAULT '0',
  PRIMARY KEY (`id`),
  UNIQUE KEY `nom` (`nom`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8 COLLATE=utf8_general_ci; -->

<H1>Première étape : le personnage</H2>

<strong>code --> </strong>
<!-- class Personnage
{
  private $_id,
          $_degats,
          $_nom;

<H2 Les fonctionnalités d'un personnage : </H2>

Un personnage doit pouvoir : 
Frapper un autre personnage ;

<strong>code --> </strong>
<!-- public function frapper(Personnage $perso)
{
- Avant tout : vérifier qu'on ne se frappe pas soi-même.
- Si c'est le cas, on stoppe tout en renvoyant une valeur signifiant que le personnage ciblé est le personnage qui attaque.
- On indique au personnage frappé qu'il doit recevoir des dégâts
}.

recevoir des dégâts.         

<strong>code --> </strong>
<!-- public function recevoirDegats()
{
    - On augmente de 5 les dégâts
    - Si on a 100 de dégâts ou plus, la méthode renverra une valeur signifiant que le personnage a été tué.
    - Sinon, elle renverra une valeur signifiant que le personnage a bien été frappé.
}
} -->

Ensuite, à certains moments dans le code, il est dit que la méthode « renverra une valeur signifiant que le personnage a bien été frappé » par exemple. Qu'est-ce que cela peut bien signifier ? Ce genre de commentaire laissera place à des constantes de classe (si vous l'aviez deviné, bien joué !). Si vous regardez bien le code, vous verrez 3 commentaires de la sorte :

<!-- Méthodefrapper(): « [...] renvoyant une valeur signifiant que le personnage ciblé est le personnage qui attaque » → la méthode renverra la valeur de la constanteCEST_MOI;

// MéthoderecevoirDegats(): « la méthode renverra une valeur signifiant que le personnage a été tué » → la méthode renverra la valeur de la constantePERSONNAGE_TUE;

// MéthoderecevoirDegats(): « elle renverra une valeur signifiant que le personnage a bien été frappé » → la méthode renverra la valeur de la constantePERSONNAGE_FRAPPE. -->

<strong>code --> </strong>
<!-- const CEST_MOI = 1;
const PERSONNAGE_TUE = 2;
const PERSONNAGE_FRAPPE = 3;

Les getters et setters
Actuellement, les attributs de nos objets sont inaccessibles. Il faut créer des getters pour pouvoir les lire, et des setters pour pouvoir modifier leurs valeurs. 

<strong>code --> </strong>
<!-- public function degats()
  {
    return $this->_degats;
  }
  public function id()
  {
    return $this->_id;
  }
  public function nom()
  {
    return $this->_nom;
  }
  public function setDegats($degats)
  {
    $degats = (int) $degats;
    if ($degats >= 0 && $degats <= 100)
    {
      $this->_degats = $degats;
    }
  }
  public function setId($id)
  {
    $id = (int) $id;
    if ($id > 0)
    {
      $this->_id = $id;
    }
  }
  public function setNom($nom)
  {
    if (is_string($nom))
    {
      $this->_nom = $nom;
    }
  }

Hydrater ses objets
Deuxième point essentiel que nous allons ré-exploiter dans ce TP : l'hydratation.

Je n'ai pas d'explication supplémentaire à ajouter, tout est dit dans le précédent chapitre. La méthode créée dans ce dernier est d'ailleurs réutilisable ici. 

<strong>code --> </strong>
<!--   public function hydrate(array $donnees)
  {
    foreach ($donnees as $key => $value)
    {
      $method = 'set'.ucfirst($key);
      if (method_exists($this, $method))
      {
        $this->$method($value);
      }
    }
  }

  Il ne manque plus qu'à implémenter le constructeur pour qu'on puisse directement hydrater notre objet lors de l'instanciation de la classe. Pour cela, ajoutez un paramètre :$donnees. Appelez ensuite directement la méthodehydrate().

<strong>code --> </strong>
<!--   public function __construct(array $donnees)
  {
    $this->hydrate($donnees);
  }  

<H1>Seconde étape : stockage en base de données</H1>

<H1>Troisième étape : utilisation des classes</H1>