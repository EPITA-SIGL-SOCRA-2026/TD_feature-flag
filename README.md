# TP — Feature Toggle avec GrowthBook

## Objectif

Mettre en place un serveur GrowthBook en local et utiliser un **feature toggle** ciblé en fonction d’un utilisateur simulé.

---

## Étapes

### 1. Lancer GrowthBook en local

Lancez l’environnement :

```bash
docker-compose up -d
```

Accédez à l’interface admin sur [http://localhost:3000](http://localhost:3000)

---

### 2. Créer un projet et un SDK

Dans l’interface GrowthBook :

- Créez un projet vide (nom au choix)
- Allez dans **SDK Configuration**
- Créez un SDK client (React) → suivez les instructions dans l'interface

---

### 3. Simuler une page de login (hard-coded)

Créez une petite page React avec **deux utilisateurs au choix**, par exemple :

```ts
const users = [
  { id: 1, name: "Alice" },
  { id: 2, name: "Bob" },
];
```

Affichez des boutons pour se connecter comme l’un ou l’autre utilisateur. Stockez l’utilisateur sélectionné dans le `state`.

---

### 4. Intégrer GrowthBook côté frontend

Suivez le guide depuis l'interface de growthbook sur localhost:3000

---

### 5. Créer une feature toggle ciblée

Dans l’interface GrowthBook :

- Ajoutez une feature nommée `eco-design`, `party-time` ou autre
- Type : boolean
- Règle : activer uniquement si `id == 1`

---

### 6. Utiliser `isOn` pour adapter l’interface

```ts
const isEco = gb.isOn("eco-design");

return (
  <div className={isEco ? "eco" : ""}>
    <h1>Bienvenue {user.name}</h1>
    {isEco && <p>🌱 Éco-design activé !</p>}
  </div>
);
```
