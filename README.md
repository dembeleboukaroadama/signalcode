# signalcode


##LES REQUETES

-------------------------------------------le profil------------------------------------------------------------------------------------
SELECT username, email_user, photo FROM user, profi WHERE user.id_profil=profi.id_profil AND id_user=GET[‘id’];

-------------------------------------------add experience------------------------------------------------------
INSERT INTO experiences(id_experience,nom_compagnie,localisation, dte_debut, date_fin) VALUES(‘’’’,  ‘’ nom_compagnie’’,  ‘’localisation’’, ‘’date_debut’’ , ‘’date_fin ‘’) ;

-------------------------------------------add education-------------------------------------------------------------------------------
INSERT INTO ecoles(id_ecole, nom_ecole, date_debut, date_fin) VALUE(‘’’’, ‘’nom_ecole’’, ‘’date_debut’’,’’date_fin’’) ;

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------add languge-------------------------------------------------------------------------------------------------------------------------
INSERT INTO langage(id_langage, nom_langage, id_synatxe) VALUES (‘’’’, ‘’nom_langage’’,’’id_syntaxe’’) ;

-----------------------------------add tool-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
INSERT INTO tools(id_tool, nom_tool, id_langage) VALUES (‘’’’, ‘’nom_tool’’, ‘’id_langage’’) ;

-------------------------------------daily challenges----------------------------------------------------------------------------------------------------------
 SELECT titre_challenge, statut, nb_inscrits, date, nb_like, valeur FROM challenge, recompense, exercices
WHERE challenge.id_exercice=exercices.id_exercice 
AND exercices.id_recompense=recompense.id_recompense
AND id_challenge=GET[‘id’];


--------------------------------------------------arcade--------------------------------------------------------------------------------
SELECT COUNT(*) FROM exercices;

-les sections à l’interieur de arcade

SELECT nom_section FROM section, rubriques
WHERE section.id_rubrique=rubriques.id_rubrique
AND rubriques.id_rubrique=GET[‘id’];

-------------------------------les exercices à l’intérieur des section-------------------------------------------------------------------------

SELECT id_exercice as exercice FROM exercices, section
WHERE section.id_section=exercices.id_section
AND section.id_section=GET[‘id’];

----------------------------------------l’interieur de l’exercice-------------------------------------------------------------------------------------------------
SELECT nom_exercice,description, contenu, nom_langage, valeur, nb_inscrits, nb_point , type_difficulte
FROM exercices, langage, recompense, tests, points
WHERE exercices.id_langage=langage.id_langage
AND exercices.id_recompense=recompense.id_recompense
AND exercices.id_test=tests.id_test
AND exercices.id_point=points.id_point
AND exercice.id_difficulte=difficultes.id_difficulte
AND id_exercice=GET[‘id’];

---------------------------------------------------------------------solutions-----------------------------------------------------------
SELECT contenu_solution,nom_exercice,duree,date,vote,nb_solution, username, email_user, photo  
FROM solutions, user, profi, exercices
WHERE solutions.id_user=user.id_user
AND solutions.id_exercice=exercices.id_exercice
AND user.id_profil=profi.id_profil
AND id_solution=GET[‘id’];



--------------------------------------------------------------comentaires-------------------------------------------------------------

SELECT description, nb_vote , date, titre_poste, username, email_user
FROM commentaires, postes, user
WHERE commentaires.id_user=user.id_user
AND commentaires.id_poste=postes.id_poste
AND commentaires.id_commentaire=GET['id'];

-------------------------------------------------------------------------reactions--------------------------------------------------------

SELECT titre_poste, username, email_user, description_reaction
FROM reactions, postes, user
WHERE reactions.id_user=user.id_user
AND reactions.id_poste=postes.id_poste
AND id_reaction=GET['id'];

------------------------------------------------------------------------tournois--------------------------------------------------------------------

SELECT nom_tournois, nb_inscrits, valeur, duree
FROM tournois, recompense, tournois_type, type
WHERE tournois_type.id_type=tournois_type.id_tournois
AND tournois.id_recompense=recompense.id_recompense
AND type.id_type=GET[‘id’];






-------------------------------------------------------------CREATE--------------------------------------------------------------------------

INSERT INTO tournois(id_tournois, nom_tournois, etat, id_exercice, duree, id_commentaire, nb_inscrits, id_recompense) ;











-----
