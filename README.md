# Le battant — POC hero volet 3D

POC d'un hero scroll-driven pour [Le battant](https://lebattant.netlify.app). Volet battant aluminium photo-réaliste qui s'ouvre à mesure que tu scrolles. Caméra qui orbite + zoom.

## 🌐 Live

<https://hermanvanel-ui.github.io/le-battant-volet-poc/>

## 🪟 Ce qu'il y a dans la boîte

- **Volet battant 2 panneaux** procédural (cadre alu + 14 lamelles horizontales + 3 paumelles + poignées)
- **Animation au scroll** : les 2 panneaux s'ouvrent à 117° (overshoot easeOutBack)
- **Texture alu brossé** générée procéduralement via canvas (lignes verticales aléatoires + gradient)
- **Matériau MeshPhysicalMaterial** : metalness 0.55, roughness 0.4, clearcoat 0.55, envMapIntensity 1.5
- **Mur arrière** avec fenêtre cadre alu sombre, fond emissive orange chaud qui s'intensifie quand les volets s'ouvrent
- **3-point lighting** : spot warm + fill cool + rim rouge sang (accent Le battant)
- **HDRI** Venice sunset (reflets warm sur l'alu)
- **Bloom post-process** (UnrealBloomPass) pour le glow
- **Tonemapping** ACES Filmic
- **Sol béton ciré** (clearcoat subtil pour reflets discrets)
- **Lenis smooth scroll**
- **HUD** : brand top-left (Pacifico), dots de progression, hint scroll

## 🎯 Cas d'usage : hero V2 Le battant

À intégrer dans le hero de la V2 du site `lebattant.fr`. Le visiteur arrive, voit les volets fermés, scrolle un peu → ils s'ouvrent en révélant la lumière de l'intérieur. Texte de promesse défile en parallèle (sur-mesure, alu 10 ans laquage, fabriqué France, devis 48h, CTA).

→ Distinctif de Technal/Reynaers/Schüco qui ont tous des sites lambda. **Argument de vente pour Simon** + démarche premium qui justifie le prix.

## 📦 Stack

- Three.js 0.166 (importmap ESM)
- Lenis 1.1.13 (smooth scroll)
- EffectComposer + UnrealBloomPass + OutputPass (post-process)
- RGBELoader (HDRI)
- HDRI : `venice_sunset_1k.hdr` (Three.js examples CDN)
- Single HTML file, ~700 lignes

## 🎨 Palette

- `--noir` #0a0a0d
- `--creme` #F5F0E1
- `--rouge` #C5322D (accent, rim light, CTA, dots actifs)
- `--vert-volet` #8FAF89 (couleur des volets — palette officielle Le battant)
- `--vert-deep` #4A6347

## 🚀 Pour aller plus loin

- Remplacer les primitives du volet par un **vrai modèle glTF** (Blender → export Draco). Utiliser le skill `blender-web-pipeline`.
- Ajouter des **vraies textures PBR** Polyhaven (au lieu du brossage canvas-generated) — repo `3d-pbr-library` à créer.
- Ajouter un **son subtil** au moment où les volets s'ouvrent (grincement bois + cliquetis paumelles).
- **Variante coulissant** : panneaux qui glissent latéralement au lieu de battre.
- Intégrer dans la **V2 du site** comme hero direct.

## ⚠️ Honnêteté

C'est un POC. Le rendu est **propre** mais reste du **procédural** — pour un vrai photoréalisme niveau Bruno Simon, il faudra :
1. Vrais modèles glTF (modélisés Blender)
2. Textures PBR multi-maps (Polyhaven)
3. Possiblement migration sur React Three Fiber pour composer plus proprement

Voir le repo de skill `webdesign-3d-scroll-experience` (références/integration-existing-site.md) pour le pipeline complet.
