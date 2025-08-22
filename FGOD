function () {
  let autoFarmInterval = null;

  function startAutoFarm() {
    const button = $("#FarmGodAutoButton");

    if (autoFarmInterval) {
      clearInterval(autoFarmInterval);
      autoFarmInterval = null;
      button.text("Start Auto-Farm");
      UI.InfoMessage("Auto-farm stopped.");
      return;
    }

    button.text("Stop Auto-Farm");
    UI.InfoMessage("Auto-farm started...");

    autoFarmInterval = setInterval(() => {
      const $nextTarget = $(".farmGod_icon").first();
      if ($nextTarget.length) {
        $nextTarget.trigger("click");
      } else {
        clearInterval(autoFarmInterval);
        autoFarmInterval = null;
        button.text("Start Auto-Farm");
        UI.InfoMessage("All farms processed.");
      }
    }, 400);
  }

  function addAutoFarmButton() {
    if ($("#FarmGodAutoButton").length > 0) return; // avoid duplicates

    const $targetTable = $(".farmGodContent table.vis").first();
    if ($targetTable.length === 0) {
      console.warn("Farm table not found. Auto-farm button not inserted.");
      return;
    }

    const $row = $(`
      <tr>
        <td colspan="4" style="text-align:center; padding:5px;">
          <button id="FarmGodAutoButton" class="btn">Start Auto-Farm</button>
        </td>
      </tr>
    `);

    $row.find("#FarmGodAutoButton").on("click", startAutoFarm);

    $targetTable.find("tr").eq(0).after($row); // insert after header row
  }

  // Ensure DOM is ready
  $(document).ready(() => {
    addAutoFarmButton();
  });
})();
