# 2026 10 01 — SGBD cours 8 - sous-requêtes

Les pilotes qui n’ont pas volé

```sql
SELECT numpil FROM pilote
WHERE numpil NOT IN (SELECT numpil FROM vol);
```

Les noms de pilotes qui ont effectué le vol avec la jointure

```sql
SELECT nompil FROM pilote
INNER JOIN vol USING(numpil);

-- AVEC SOUS REQUÊTE --

SELECT numpil FROM pilote
WHERE numpil IN (SELECT numpil FROM vol);
```

elle est longue la consigne hein

```sql
SELECT idmembres, nommembre, prenomembre FROM membre m
INNER JOIN inscrire p
ON m.id_memb = p.id_memb
GROUP BY id_membre, nommembre, prenommembre 
HAVING COUNT(DISTINCT idactivite) = (SELECT COUNT(DISTINCT inactivité) FROM activité);
```

pareil mais sans jointure

```sql
SELECT idmembres, nommembre, prenomembre FROM membre m
WHERE SELECT COUNT(DISTINCT id_activ) FROM inscrire 
WHERE inscrire.id_memb = m.id_memb) = (SELECT COUNT(DISTINCT id_activ) FROM activite);
```

 