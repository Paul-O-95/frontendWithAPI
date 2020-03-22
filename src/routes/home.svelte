<script>
  import axios from "axios";
  let data = [];
  let inputFirstname1 = "";
  let inputLastname1 = "";
  let inputFirstname2 = "";
  let inputLastname2 = "";

  const compare = async event => {
    event.preventDefault();
    let res = await axios.post(
      "https://62806eb5-9d24-4288-ab86-225eaf036470.mock.pstmn.io/compare"
    );
    let result = res.data.inputs;
    data = [result, ...data];
    console.log(data);
    location.replace("http://localhost:3000/result");
  };
</script>

<div class=" container-fluid">
  <h2 class="text-center">Comparison Test</h2>
  <div class="row">
    <div class="col-md col-sm-12">
      <!-- Default form register -->
      <form
        class="text-center border border-light p-5"
        on:submit|preventDefault={compare}>
        <h3>Student One</h3>
        <div class="form-row mb-4">

          <div class="col-md col-sm-12 mb-4">
            <!-- First name -->
            <input
              type="text"
              name="name1"
              bind:value={inputFirstname1}
              id="defaultRegisterFormFirstName"
              class="form-control"
              placeholder="First name" />
          </div>
          <div class="col-md col-sm-12 mb-4">
            <!-- Last name -->
            <input
              name="1"
              type="text"
              bind:value={inputLastname1}
              id="defaultRegisterFormLastName"
              class="form-control"
              placeholder="Last name" />
          </div>

          <!-- File Upload -->
          <div class="input-group">
            <!-- <div class="input-group-prepend col-sm-12">
              <span class="input-group-text " id="inputGroupFileAddon01">
                Upload
              </span>
            </div> -->
            <div class="custom-file col-sm-12">
              <input
                type="file"
                class="custom-file-input"
                id="inputGroupFile01"
                aria-describedby="inputGroupFileAddon01" />
              <label class="custom-file-label text-left" for="inputGroupFile01">
                Choose file
              </label>
            </div>
          </div>
        </div>

        <h3>Student Two</h3>
        <div class="form-row mb-4">
          <div class="col-md col-sm-12 mb-4">
            <!-- First name -->
            <input
              name="name2"
              type="text"
              bind:value={inputFirstname2}
              id="defaultRegisterFormFirstName"
              class="form-control"
              placeholder="First name" />
          </div>
          <div class="col-md col-sm-12 mb-4">
            <!-- Last name -->
            <input
              name="2"
              type="text"
              bind:value={inputLastname2}
              id="defaultRegisterFormLastName"
              class="form-control"
              placeholder="Last name" />
          </div>

          <!-- File Upload -->
          <div class="input-group">
            <!-- <div class="input-group-prepend col-sm-12">
              <span class="input-group-text " id="inputGroupFileAddon01">
                Upload
              </span>
            </div> -->
            <div class="custom-file col-sm-12">
              <input
                type="file"
                class="custom-file-input"
                id="inputGroupFile01"
                aria-describedby="inputGroupFileAddon01" />
              <label class="custom-file-label text-left" for="inputGroupFile01">
                Choose file
              </label>
            </div>
          </div>
        </div>

        <button class="btn blue-gradient btn-block">Compare</button>
      </form>
      <!-- Default form register -->
    </div>
  </div>
</div>
