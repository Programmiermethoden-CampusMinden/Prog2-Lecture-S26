# Swing Events

> [!IMPORTANT]
>
> <details open>
> <summary><strong>🎯 TL;DR</strong></summary>
>
> In Swing-Komponenten werden Events ausgelöst, wenn der User mit den
> Komponenten interagiert.
>
> Zur Bearbeitung der Events kann man Listener bei den Komponenten
> registrieren, die bei Auftreten eines Events benachrichtigt werden
> (Observer-Pattern: Die Observer werden in Swing "Listener" genannt).
>
> Es gibt für alle möglichen Formen von Interaktion mit Komponenten
> vordefinierte Interfaces für die Event-Listener. Da man hier wie
> üblich immer alle Methoden implementieren muss, selbst wenn man nur
> auf wenige Events reagieren möchte, gibt es zusätzlich sogenannte
> "Adapter": Dies sind Klassen, die das jeweilige
> Event-Listener-Interface mit leeren Methodenrümpfen implementieren.
> Bei Nutzung der Adapter-Klassen müssen dann nur noch die benötigten
> Methoden überschrieben werden.
>
> </details>

> [!TIP]
>
> <details open>
> <summary><strong>🎦 Videos</strong></summary>
>
> -   [VL Swing Events](https://youtu.be/Un-FS88__VU)
> -   [Demo Swing Events und Listener](https://youtu.be/hjchoDaqcWY)
> -   [Demo MouseListener
>     vs. MouseAdapter](https://youtu.be/GaKMBAXY19w)
>
> </details>

## Reaktion auf Events: Anwendung Observer-Pattern

-   Swing-GUI läuft in Dauerschleife
-   Komponenten registrieren Ereignisse (Events):
    -   Mausklick
    -   Tastatureingaben
    -   Mauszeiger über Komponente
    -   ...
-   Reaktion mit passendem Listener: Observer Pattern!

<p align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Programmiermethoden-CampusMinden/Prog2-Lecture/_s26/lecture/gui/images/ActionListener_inv.png" /><img src="https://raw.githubusercontent.com/Programmiermethoden-CampusMinden/Prog2-Lecture/_s26/lecture/gui/images/ActionListener.png" width="80%" /></picture></p>

=\> Observer aus dem Observer-Pattern!

In Swing werden die "Observer" als "Listener" bezeichnet.

``` java
component.addActionListener(ActionListener);
component.addMouseListener(MouseListener);
```

## Arten von Events

<p align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Programmiermethoden-CampusMinden/Prog2-Lecture/_s26/lecture/gui/images/EventListener_inv.png" /><img src="https://raw.githubusercontent.com/Programmiermethoden-CampusMinden/Prog2-Lecture/_s26/lecture/gui/images/EventListener.png" width="80%" /></picture></p>

Es gibt für alle möglichen Input-Arten eine Ableitung von
`java.util.EventListener`, beispielsweise für Maus- oder
Tastaturereignisse oder wenn ein Element den Fokus bekommt und viele
weitere.

## Details zu Listenern

-   Ein Listener kann bei mehreren Observables registriert sein:

    ``` java
    Handler single = new Handler();
    singleButton.addActionListener(single);
    multiButton.addActionListener(single);
    ```

-   Ein Observable kann mehrere Listener bedienen:

    ``` java
    multiButton.addActionListener(new Handler());
    multiButton.addActionListener(new Handler());
    ```

-   Sequentielles Abarbeiten der Events bzw. Benachrichtigung der
    Observer

<p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/Prog2-Lecture/blob/master/lecture/gui/src/events/ListenerDemo.java">Demo: events.ListenerDemo</a></p>

## Wie komme ich an die Daten eines Events?

<p align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Programmiermethoden-CampusMinden/Prog2-Lecture/_s26/lecture/gui/images/EventObject_inv.png" /><img src="https://raw.githubusercontent.com/Programmiermethoden-CampusMinden/Prog2-Lecture/_s26/lecture/gui/images/EventObject.png" width="80%" /></picture></p>

**Event-Objekte**: Quelle des Events plus aufgetretene Daten

<p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/Prog2-Lecture/blob/master/lecture/gui/src/events/MouseListenerDemo.java">Demo: events.MouseListenerDemo</a></p>

## Listener vs. Adapter

-   Vielzahl möglicher Events
-   Jeweils passendes Event-Objekt u. Event-Listener-Interface
-   Oft nur wenige Methoden, u.U. aber viele Methoden

=\> Bei Nutzung eines Event-Listeners müssen immer **alle** Methoden
implementiert werden (auch nicht benötigte)!

Abhilfe: **Adapter**-Klassen:

-   Für viele Event-Listener-Interfaces existieren Adapter-Klassen
-   Implementieren jeweils ein Interface
-   Alle Methoden mit **leerem** Body vorhanden

=\> Nur benötigte Listener-Methoden überschreiben.

<p align="right"><a href="https://github.com/Programmiermethoden-CampusMinden/Prog2-Lecture/blob/master/lecture/gui/src/events/MouseAdapterDemo.java">Demo: events.MouseAdapterDemo</a></p>

## Exkurs: Nützliches zu Swing

Über Swing wurde prinzipiell bereits im ersten Semester gesprochen,
deshalb wird hier in Prog2 nur der Zusammenhang mit dem
[Observer-Pattern](../pattern/observer.md) hergestellt.

Wenn Sie Ihr Wissen zu Swing auffrischen wollen, hier vier nützliche
Sessions zu Swing:

-   [Swing Basics](./swing1-basics.md)
-   [Nützliche Widgets](./swing2-widgets.md)
-   [Layouts und -Manager](./swing3-layouts.md)
-   [Java2D](./swing6-java2d.md)

## Wrap-Up

Observer-Pattern in Swing-Komponenten:

-   Events: Enthalten Source-Objekt und Informationen
-   Event-Listener: Interfaces mit Methoden zur Reaktion
-   Adapter: Listener mit leeren Methodenrümpfen

> [!TIP]
>
> <details open>
> <summary><strong>📖 Zum Nachlesen</strong></summary>
>
> -   Oracle Corporation ([2024](#ref-Java-SE-Tutorial))
> -   Ullenboom ([2021, Kap. 18](#ref-Ullenboom2021))
>
> </details>

> [!NOTE]
>
> <details >
> <summary><strong>✅ Lernziele</strong></summary>
>
> -   k2: Unterschied zwischen den Listenern und den entsprechenden
>     Adaptern
> -   k3: Anwendung des Observer-Pattern, beispielsweise als Listener in
>     Swing, aber auch in eigenen Programmen
> -   k3: Nutzung von ActionListener, MouseListener, KeyListener,
>     FocusListener
>
> </details>

------------------------------------------------------------------------

> [!NOTE]
>
> <details >
> <summary><strong>👀 Quellen</strong></summary>
>
> <div id="refs" class="references csl-bib-body hanging-indent">
>
> <div id="ref-Java-SE-Tutorial" class="csl-entry">
>
> Oracle Corporation. 2024. „The Java Tutorials".
> <https://docs.oracle.com/javase/tutorial/>.
>
> </div>
>
> <div id="ref-Ullenboom2021" class="csl-entry">
>
> Ullenboom, C. 2021. *Java ist auch eine Insel*. 16. Aufl.
> Rheinwerk-Verlag.
> <https://openbook.rheinwerk-verlag.de/javainsel/index.html>.
>
> </div>
>
> </div>
>
> </details>

------------------------------------------------------------------------

<p align="center"><img src="https://licensebuttons.net/l/by-sa/4.0/88x31.png"  /></p>

Unless otherwise noted, this work is licensed under CC BY-SA 4.0.

<blockquote><p><sup><sub><strong>Last modified:</strong> 16fc70d 2026-04-11 reformat markdown<br></sub></sup></p></blockquote>
