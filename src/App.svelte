<script>
  import Comp1 from "./lib/Comp1.svelte";
  import Comp2 from "./lib/Comp2.svelte";
  import TopMenu from "./lib/TopMenu.svelte";
  import FlexShow from "./lib/FlexShow.svelte";
  import AnimeGif from "./lib/AnimeGif.svelte";
  import { display } from "./lib/select_values.svelte";
  import { flex_direction } from "./lib/select_values.svelte";
  import { just_content } from "./lib/select_values.svelte";

  import DetectMessage from './lib/Detector.svelte'


  // Объект для биндинга выбранных в select'ах значений
  let flexvals = $state({
    disp: "block",
    direct: "row",
    just_content: "flex-start",
  });

</script>

<main>

  <div class="container">
    <h1>START</h1>

    <div class="combos">
      <div>
        <select bind:value={flexvals.disp}>
          {#each display as item}
            <option>
              {item}
            </option>
          {/each}
        </select>
      </div>

      <div>
        <select bind:value={flexvals.direct}>
          {#each flex_direction as item}
            <option>
              {item}
            </option>
          {/each}
        </select>
      </div>

      <div>
        <select bind:value={flexvals.just_content}>
          {#each just_content as item}
            <option>
              {item}
            </option>
          {/each}
        </select>
      </div>
    </div>

    <div>
      <FlexShow selected={flexvals} />
      <AnimeGif />
    </div>
  </div>
</main>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: 'Poppins', sans-serif; /* Используем округлый шрифт */
  }

  main {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh; /* Занимает всю высоту экрана */
    background-color: #f7f7f7; /* Светлый фон для всего приложения */
  }

  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #ffffff; /* Белый фон */
    padding: 20px;
    border-radius: 15px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.2);
  }

  .combos {
    display: flex;
    gap: 10px; /* Промежутки между селектами */
    margin-bottom: 20px; /* Отступ снизу */
  }

  select {
    padding: 10px;
    border: 2px solid #333; /* Темная граница */
    border-radius: 10px; /* Округлые углы */
    background-color: #f7f7f7; /* Светло-серый фон для селектов */
    font-size: 16px;
    transition: border-color 0.3s ease;
  }

  select:hover {
    border-color: #555; /* Изменение цвета границы при наведении */
  }

  h1 {
    margin-bottom: 20px; /* Отступ снизу для заголовка */
    color: #333; /* Темный цвет для заголовка */
  }
</style>