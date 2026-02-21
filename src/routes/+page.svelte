<script lang="ts">
    import "../app.css";
    import { onMount, onDestroy } from "svelte";
    import TripsSection from "$lib/components/TripsSection.svelte";
    import type { Trip } from "$lib/types/trip";

    interface Slide {
        image: string;
        title: string;
        subtitle: string;
        link: string;
    }

    const trips: Trip = [
        {
            title: "Norwegia - zorza polarna",
            date: "Październik 2025 - Marzec 2026",
            description:
                "Stworzony z myślą o osobach, które dopiero rozpoczynają swoją przygodę z via ferratami. Dzięki niemu krok po kroku poznasz wszystkie kluczowe aspekty bezpiecznego i świadomego poruszania się po tych ekscytujących trasach. Można zabrać młodzież 🙂",
            link: "/norwegia-tromso-zorza",
            button: "Zapisz się na wyprawę",
            image: "/img/norway.jpg",
        },
        {
            title: "Lofoty - dzień polarny",
            date: "Czerwiec - Lipiec 2025",

            description:
                "Kameralna wyprawa na północ w poszukiwaniu zorzy polarnej, arktycznych krajobrazów i dzikiej natury.",
            link: "/norwegia-lofoty",
            button: "Zapisz się na wyprawę",
            image: "/img/lofoty.jpg",
        },
        {
            title: "Islandia - lodowce i wulkany",
            date: "Sierpień 2025",

            description:
                "Kameralna wyprawa na północ w poszukiwaniu zorzy polarnej, arktycznych krajobrazów i dzikiej natury.",
            link: "/islandia",
            button: "Zapisz się na wyprawę",
            image: "../img/iceland.jpg",
        },
    ];

    // Lista zdjęć bannerów

    let slides: Slide[] = [
        {
            image: "/img/baner_1.jpg",
            title: "Przygoda zaczyna się na północy",
            subtitle: "Norwegia - zorza polarna",
            link: "/norwegia-tromso-zorza",
        },
        {
            image: "/img/baner_2.jpg",
            title: "Przygoda zaczyna się na północy",
            subtitle: "Lofoty - dzień polarny",
            link: "/norwegia-lofoty",
        },
        {
            image: "/img/baner_3.jpg",
            title: "Przygoda zaczyna się na północy",
            subtitle: "Islandia - lodowce i wulkany",
            link: "/islandia",
        },
        {
            image: "/img/baner_4.jpg",
            title: "Przygoda zaczyna się na północy",
            subtitle: "Szwecja - magiczne lasy",
            link: "/szwecja",
        },
    ];

    let current = 0;
    let interval: ReturnType<typeof setInterval>;

    onMount(() => {
        interval = setInterval(() => {
            current = (current + 1) % slides.length;
        }, 5000); // zmiana co 5 sekund
    });

    onDestroy(() => {
        clearInterval(interval);
    });

    function goTo(index: number) {
        current = index;
    }
</script>

<section class="banner-slider">
    {#each slides as slide, i}
        <div
            class="slide {i === current ? 'active' : ''}"
            style="background-image: url({slide.image})"
        >
            <div class="overlay">
                <h1>{slide.title}</h1>
                <p>{slide.subtitle}</p>
                <a class="button" href={slide.link}>Zapisz się na wyprawę</a>
            </div>
        </div>
    {/each}
</section>

<section class="intro-text">
    <div class="container">
        <p>
            Marzysz, żeby zobaczyć jak wygląda życie na dalekiej Północy?
            Zastanawiasz się jak to jest, kiedy Słońce nie chowa się pod
            horyzont przez wiele tygodni lub... w ogóle się spod niego nie
            wyłania? Do tego surowy klimat, szybko zmieniająca się pogoda,
            zapierające dech w piersi widoki, bogactwo flory i fauny (liczne
            łosie, renifery, orły, foki, maskonury), a przede wszystkim
            niesamowite zorze polarne rozświetlające Północne niebo. Tak właśnie
            wygląda Północ, którą my pokochaliśmy już dawno temu, a dzisiaj
            chcemy się podzielić nią razem z Wami. Zapraszamy Was na nasze
            kameralne wycieczki w okolice koła podbiegunowego, gdzie otwieramy
            dla Was wrota do niezwykłego świata Arktyki. Dołącz już dzisiaj do
            naszej Arktycznej Przygody.
        </p>
        <p class="signature">
            Natalia i Jarek<br />
            - Wasi przewodnicy po Arktyce
        </p>
    </div>
</section>


<TripsSection {trips} />

<section class="section features">
    <h2>Co Nas Wyróżnia</h2>

    <div class="features-grid">
        <div class="feature">
            <h3>♦ Doświadczenie</h3>
            <p>
                Wszystko zaczęło się 6 lat temu. Arktyka stała się naszym drugim
                domem. Radzimy sobie z surowym klimatem, śnieżycami i zmienną
                pogodą.
            </p>
        </div>

        <div class="feature">
            <h3>♦ Autorski program</h3>
            <p>
                Pokazujemy nie tylko popularne miejsca, ale też ukryte spoty, do
                których nie docierają zwykli turyści.
            </p>
        </div>

        <div class="feature">
            <h3>♦ Kameralne grupy</h3>
            <p>
                Maksymalnie 8 osób – większa mobilność, lepsza integracja i
                komfort podróży.
            </p>
        </div>

        <div class="feature">
            <h3>♦ 100% Zorzy</h3>
            <p>
                Dzięki doświadczeniu i znajomości pogody wszystkie nasze grupy
                widziały zorzę polarną.
            </p>
        </div>

        <div class="feature">
            <h3>♦ Atrakcyjna oferta</h3>
            <p>
                Program jest intensywny i dopracowany, aby każda złotówka była
                warta tej wyprawy.
            </p>
        </div>

        <div class="feature">
            <h3>♦ Zadowolenie Uczestników</h3>
            <p>
                Największą nagrodą są pozytywne opinie uczestników naszych
                arktycznych wypraw.
            </p>
        </div>
    </div>

    <div class="cta">
        <a href="/opinie" class="button">Poczytaj Opinie</a>
    </div>
</section>
