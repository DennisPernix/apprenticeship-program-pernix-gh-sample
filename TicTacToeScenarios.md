### **Test-Driven Development (TDD)**

Historia de Usuario 1: Inicio del Juego

Objetivo TDD: Garantizar que el estado inicial del juego sea correcto.

Pruebas:

Dado que inicio una nueva partida, el tablero debe crearse como una matriz 3x3 vacía.
Dado que el jugador selecciona “X”, el turno inicial debe ser “X”.
Dado que el jugador selecciona “O”, el turno inicial debe ser “O”.
Al iniciar el juego, el estado debe ser EN_PROGRESO.

Código:

shouldInitializeEmptyBoard()
shouldSetInitialTurnToSelectedPlayer()
shouldSetGameStatusToInProgress()

Historia de Usuario 2: Realizar un Movimiento

Objetivo TDD: Validar reglas básicas de colocación y turnos.

Pruebas:

Al seleccionar una casilla vacía, se debe colocar la marca del jugador actual.
No se debe permitir jugar en una casilla ocupada.
Después de un movimiento válido, el turno debe cambiar al otro jugador.
El tablero solo debe modificarse cuando el movimiento sea válido.

Código:

shouldPlaceMarkInEmptyCell()
shouldNotAllowMoveInOccupiedCell()
shouldSwitchTurnAfterValidMove()
shouldNotSwitchTurnAfterInvalidMove()

Historia de Usuario 3: Determinación de Ganador o Empate

Objetivo TDD: Asegurar la lógica de finalización del juego.

Pruebas:

Dado un tablero con tres marcas iguales en una fila, debe declararse un ganador.
Dado un tablero con tres marcas iguales en una columna, debe declararse un ganador.
Dado un tablero con tres marcas iguales en una diagonal, debe declararse un ganador.
Dado un tablero lleno sin combinaciones ganadoras, debe declararse empate.
Una vez terminado el juego, no se deben permitir más movimientos.

Código:

shouldDetectWinnerByRow()
shouldDetectWinnerByColumn()
shouldDetectWinnerByDiagonal()
shouldDeclareDrawWhenBoardIsFull()
shouldBlockMovesAfterGameEnds()

Historia de Usuario 4: Reiniciar el Juego

Objetivo TDD: Restablecer completamente el estado del sistema.

Pruebas:

Al reiniciar el juego, el tablero debe quedar vacío.
El estado del juego debe volver a EN_PROGRESO.
Debe permitirse seleccionar nuevamente quién inicia (“X” u “O”).

Código:

shouldResetBoardOnRestart()
shouldResetGameStatusOnRestart()
shouldAllowPlayerSelectionAfterRestart()

Historia de Usuario 5: Interfaz de Usuario (UI) Intuitiva

Objetivo TDD: Verificar que la UI refleje el estado del dominio.

Pruebas:

La UI debe mostrar el turno actual correctamente.
La UI debe reflejar visualmente los movimientos realizados.
El mensaje de victoria o empate debe mostrarse al finalizar el juego.

Código:

shouldDisplayCurrentTurn()
shouldRenderPlayerMoveOnBoard()
shouldShowGameResultMessage()

Historia de Usuario 6: Multijugador Local

Objetivo TDD: Confirmar alternancia correcta y estado compartido.

Pruebas:

El sistema debe alternar turnos entre dos jugadores humanos.
El estado del juego debe ser consistente para ambos jugadores.
El ganador debe corresponder al jugador que realizó la última jugada válida.

Código:

shouldAlternateTurnsBetweenPlayers()
shouldAssignWinnerToCorrectPlayer()

Historia de Usuario 7: Juego contra la Computadora (IA)

Objetivo TDD: Validar comportamiento mínimo de la IA antes de optimizar.

Pruebas:

La IA debe realizar únicamente movimientos válidos.
La IA debe jugar automáticamente después del turno del jugador humano.
En dificultad fácil, la IA puede elegir cualquier casilla válida.
En dificultad difícil, la IA debe evitar perder si existe una jugada defensiva.

Código:

shouldMakeValidMoveForAI()
shouldTriggerAIMoveAfterHumanTurn()
shouldSelectAnyAvailableMoveInEasyMode()
shouldBlockWinningMoveInHardMode()

-------------------------------------------------------------------------------------------------------------------

### **Behavior-Driven Development (BDD)**

1. Interfaz de Usuario Intuitiva

Como jugador
Quiero una interfaz clara
Para entender fácilmente el estado del juego

2. Mostrar el turno actual
Given que el juego está en progreso
When cambia el turno del jugador
Then la interfaz muestra claramente el jugador actual

3. Mostrar el resultado del juego
Given que la partida finaliza
When existe un ganador o un empate
Then la interfaz muestra un mensaje con el resultado del juego

4. Modo Multijugador Local

Como jugador
Quiero jugar contra otra persona en el mismo dispositivo
Para compartir la experiencia

5. Alternar turnos entre dos jugadores

Given que dos jugadores están jugando localmente
When el jugador "X" realiza un movimiento válido
Then el turno cambia al jugador "O"

6. Juego contra la Computadora (IA)

Como jugador
Quiero jugar contra la computadora
Para practicar mis habilidades

7. Jugar contra IA en modo fácil
Given que el jugador selecciona el modo contra la computadora
And la dificultad es "fácil"
When el jugador humano realiza su movimiento
Then la computadora realiza automáticamente un movimiento válido

8. IA evita perder en modo difícil
Given que el jugador está a punto de ganar
And la dificultad es "difícil"
When es el turno de la computadora
Then la computadora bloquea la jugada ganadora del jugador