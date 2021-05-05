Voici les réponses aux questions:

a) Niveau facile

    Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
      - Réponse: 347
      - Méthode: Album.count

    Qui est l'auteur de la chanson "White Room" ?
      - Réponse: Eric Clapton
      - Méthode: Track.find_by(title: "White Room").artist
      
    Quelle chanson dure exactement 188133 milliseconds ?
      - Réponse: Perfect - Alanis Morissette
      - Méthode: Track.find_by(duration: 188133)
      
    Quel groupe a sorti l'album "Use Your Illusion II" ?
      - Réponse: Guns N Roses
      - Méthode: Album.find_by(title: "Use Your Illusion II").artist
      
b) Niveau Moyen

    Combien y a t'il d'albums dont le titre contient "Great" ? (indice)
      - Réponse: 13
      - Méthode: Album.where("title like ?", "%Great%").count
      
    Supprime tous les albums dont le nom contient "music".
      - Réponse: 4 albums supprimés
      - Méthode: Album.where("title like ?", "%music%").delete_all
      
    Combien y a t'il d'albums écrits par AC/DC ?
      - Réponse: 2
      - Méthode: Album.where(artist: "AC/DC").count
      
    Combien de chanson durent exactement 158589 millisecondes ?
      - Réponse: 0
      - Méthode: Track.where(duration: 158589).count
      
c) Niveau Difficile

  puts en console tous les titres de AC/DC.
    - Réponse: 
      For Those About To Rock (We Salute You)
      Put The Finger On You
      Lets Get It Up
      Inject The Venom
      Snowballed
      Evil Walks
      C.O.D.
      Breaking The Rules
      Night Of The Long Knives
      Spellbound
      Go Down
      Dog Eat Dog
      Let There Be Rock
      Bad Boy Boogie
      Problem Child
      Overdose
      Hell Aint A Bad Place To Be
      Whole Lotta Rosie
    - Méthode: 
      t = Track.where(artist: "AC/DC")
      t.each do |track|
        puts track.title
      end
          
  puts en console tous les titres de l'album "Let There Be Rock".
    - Réponse:
      Go Down
      Dog Eat Dog
      Let There Be Rock
      Bad Boy Boogie
      Problem Child
      Overdose
      Hell Aint A Bad Place To Be
      Whole Lotta Rosie
    - Méthode:
      tracks = Track.where(album: "Let There Be Rock")
      tracks.each do |track|
        puts track.title
      end
      
  Calcule le prix total de cet album ainsi que sa durée totale.
    - Réponse: 7.92$ ||| 40
    - Méthode:
      (tracks = )Track.where(album: "Let There Be Rock").sum(:price).round(2)/sum(:duration)/60000.round(2)
      tracks.sum(:price).round(2) ||| tracks.sum(:duration)/60000
          
  Calcule le coût de l'intégralité de la discographie de "Deep Purple".
    - Réponse: 90.09$
    - Méthode: Track.where(artist: "Deep Purple").sum(:price).round(2)
          
  Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.
    - Réponse: 32 titres modifiés
    - Méthode: 
      britney = Track.where(artist: "Eric Clapton")
      britney.each do |track|
        track.artist = "Britney Spears"
        track.save
      end     