<script>
  import { getContext } from "svelte"

  const { styleable } = getContext("sdk")
  const component = getContext("component")
  export let inactiveColor;
  export let activeColor;
  export let accentColor;

  let isActive = false;

  const handleButtonClick = () => {
    isActive = !isActive;
  };
</script>

<div use:styleable={$component.styles}>
  <div class="toggle">
    <div style="background: {isActive ? activeColor : inactiveColor};" class="toggle-button {isActive && 'toggle-button-active'}" on:click={handleButtonClick}>
      <div style="background: {accentColor};" class="toggle-inner-circle {isActive && 'toggle-inner-circle-active'}">
      </div>
    </div>
  </div>
</div>

<style>

  .toggle{
    display: flex;
    position: relative;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }


  .toggle-button {
    width: 60px;
    height: 35px;
    border-radius: 30px;
    padding: 5px;
    transition: all 200ms ease-in-out;
  }

  .toggle-button > .toggle-inner-circle {
    width: 25px;
    height: 25px;
    border-radius: 50%;
    transition: all 200ms ease-in-out;
  }

  .toggle-inner-circle-active {
    margin-left: 25px;
  }


</style>