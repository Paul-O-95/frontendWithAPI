<script>
  import axios from "axios";

  let inputs = "";
  let data = [];
  let modalArr = [];
  let grade = "";
  let display = true;

  (async () => {
    let res = await axios.get(
      "https://62806eb5-9d24-4288-ab86-225eaf036470.mock.pstmn.io/history"
    );
    data = res.data;
  })();

  async function user(id) {
    let res = await axios.get(
      "https://62806eb5-9d24-4288-ab86-225eaf036470.mock.pstmn.io/history/1"
    );
    let newmodalArr = res.data;
    modalArr = newmodalArr[id];
    console.log(id);
    console.log(modalArr.name1);

    if (modalArr.similarities <= 50) {
      return (grade = "Pass");
    }
    grade = "Fail";
    return modalArr;
  }
  async function delStudent(id) {
    let res = await axios.delete(
      `https://62806eb5-9d24-4288-ab86-225eaf036470.mock.pstmn.io/delete/${id}`
    );
    console.log(id);
    display = false;
  }
</script>

<div class="container">
  <div class="table-responsive-sm">
    <table class="table">
      <thead>
        <tr>
          <th>#</th>
          <th>Name</th>
          <th>Similarities</th>
          <th />
          <th />
        </tr>
      </thead>

      <tbody>
        {#each data as result, i}
          <tr class="">
            <th scope="row">{i + 1}</th>
            <td>{result.name1} vs {result.name2}</td>
            <td>{result.similarities}%</td>
            <td>
              <button
                on:click={() => user(i)}
                class="btn btn-sm btn-outline-info waves-effect "
                data-toggle="modal"
                data-target="#basicExampleModal">
                <i class="fas fa-info" />
              </button>
            </td>
            <td>
              <button
                class="btn btn-sm btn-danger"
                on:click={() => delStudent(result.id)}>
                <i class="fas fa-trash-alt" />
              </button>
            </td>
          </tr>
        {/each}

      </tbody>
    </table>
  </div>
</div>

<!-- Modal -->
<div
  class="modal fade"
  id="basicExampleModal"
  tabindex="-1"
  role="dialog"
  aria-labelledby="exampleModalLabel"
  aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Student Information</h5>
        <button
          type="button"
          class="close"
          data-dismiss="modal"
          aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        <h2>{modalArr.name1} and {modalArr.name2}</h2>
        <hr />
        <p>Similarities: {modalArr.similarities}</p>
        <p>Grade: {grade}</p>

      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-sm btn-success">
          <i class="fas fa-play" />
        </button>
        <button
          class="btn btn-sm btn-danger"
          on:click={() => delStudent(modalArr.id)}>
          <i class="fas fa-trash-alt" />
        </button>

      </div>
    </div>
  </div>
</div>
