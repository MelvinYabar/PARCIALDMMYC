# PARCIALMYC — Juego de Colores (Android / Kotlin)

Pequeño juego por tiempo hecho en **Kotlin** con **Android Studio**, usando **Fragments** y **Navigation Component**. El objetivo es tocar el botón del color correcto antes de que acabe el **temporizador de 30 s**. Al finalizar, se muestra la **puntuación** y se actualiza el **High Score** guardado en `SharedPreferences`. Incluye un **historial de la sesión** con `RecyclerView`.


---

## Características

* **Pantalla de Bienvenida (WelcomeFragment)**

  * Título del juego.
  * Botón **“Reglas”** → `AlertDialog` con instrucciones.
  * Botón **“Iniciar”** → navega al juego.
* **Pantalla de Juego (GameFragment)**

  * Muestra un **color objetivo** aleatorio (texto o vista coloreada).
  * **Botones por color** (p. ej., Rojo, Azul, Verde, Amarillo).
  * **Temporizador de 30 s** con `CountDownTimer`.
  * **Puntaje en vivo** y tiempo restante en pantalla.
* **Pantalla de Resultado (ResultFragment)**

  * Muestra **puntaje final**.
  * **High Score** persistente con `SharedPreferences`.
  * **RecyclerView** con historial de intentos de la **sesión actual** (no persistente) o persistente si usaste Room.
  * Botón **“Volver a jugar”** que reinicia el flujo.
* **Navegación entre fragments** con `NavHostFragment` y `nav_graph.xml`.
* **Manejo básico de ciclo de vida y estado** (restaurar puntaje/tiempo si rota la pantalla, según implementación).

### Extras posibles (marca los que implementaste)

* [ ] Sonidos (correcto/incorrecto/fin) con `SoundPool` o `MediaPlayer`.
* [ ] Animaciones (`ViewPropertyAnimator`, `MotionLayout` o `Lottie`).
* [ ] Niveles/dificultad (p. ej., **efecto Stroop**: texto “Azul” pintado de rojo, etc.).
* [ ] Persistencia con **Room** para historial y consulta de High Score global.

---

## Arquitectura

* **Single-Activity / Multi-Fragment**: `MainActivity` con `NavHostFragment`.
* **ViewModel + LiveData/StateFlow** para estado de juego (puntaje, tiempo, color actual).
* **Repositorios** (opcional) para abstracción de datos (SharedPrefs/Room).
* **UI** con `ConstraintLayout`.

```
app/
 ├─ data/
 │   ├─ prefs/HighScoreStore.kt
 │   └─ db/ (si usas Room)
 ├─ domain/ (opcional)
 ├─ ui/
 │   ├─ welcome/WelcomeFragment.kt
 │   ├─ game/GameFragment.kt
 │   ├─ result/ResultFragment.kt
 │   └─ common/
 │       ├─ GameViewModel.kt
 │       └─ model/ScoreEntry.kt
 ├─ navigation/nav_graph.xml
 └─ MainActivity.kt
```


## 👤 Autor

**Melvin Yabar Carazas** — Ingeniería de Software.

