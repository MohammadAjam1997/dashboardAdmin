<template>
  <div class="card mb-4">
    <div class="card-header pb-0">
      <h6>CRUD History</h6>
    </div>
    <div class="card-body px-0 pt-0 pb-2">
      <div class=" p-0">
        <table class="table align-items-center justify-content-center mb-0">
          <thead>
            <tr>
              <th
                class="text-uppercase text-secondary text-xxs font-weight-bolder opacity-7"
              >
                Project
              </th>
              <th
                class="text-uppercase text-secondary text-xxs font-weight-bolder opacity-7 ps-2"
              >
                Budget
              </th>
              <th
                class="text-uppercase text-secondary text-xxs font-weight-bolder opacity-7 ps-2"
              >
                Status
              </th>
              <th
                class="text-uppercase text-secondary text-xxs font-weight-bolder text-center opacity-7 ps-2"
              >
                Completion
              </th>
              <th></th>
            </tr>
          </thead>
          <tbody v-for="item in Student" :key="item.name">
            <tr>
              <td>
                <div class="d-flex px-2">
                  <div>
                    <!-- <img v-bind:src="item.img" class="avatar avatar-sm rounded-circle me-2"
                      alt="spotify"> -->
                    <!-- <img v-bind:src="'../../assets/img/small-logos/' + item.img" />  -->
                  </div>
                  <div class="my-auto">
                    <h6 class="mb-0 text-sm">{{ item.name }}</h6>
                  </div>
                </div>
              </td>
              <td>
                <p class="text-sm font-weight-bold mb-0">{{ item.price }}</p>
              </td>
              <td>
                <span class="text-xs font-weight-bold">{{ item.state }}</span>
              </td>
              <td class="align-middle text-center">
                <div class="d-flex align-items-center justify-content-center">
                  <span class="me-2 text-xs font-weight-bold">60%</span>
                  <div>
                    <div class="progress">
                      <div
                        class="progress-bar bg-gradient-info"
                        role="progressbar"
                        aria-valuenow="60"
                        aria-valuemin="0"
                        aria-valuemax="100"
                        style="width: 60%"
                      ></div>
                    </div>
                  </div>
                </div>
              </td>
              <td class="align-middle">
                <div class="dropdown">
                  <button
                    class="btn btn-secondary dropdown-toggle"
                    type="button"
                    id="dropdownMenuButton1"
                    data-bs-toggle="dropdown"
                    aria-expanded="false"
                  ></button>
                  <ul
                    class="dropdown-menu "
                    aria-labelledby="dropdownMenuButton1"
                  >
                 <li class="d-flex justify-content-center pt-3"> <button type="button" class="btn btn-outline-danger btn-sm"><i class="fa fa-regular fa-trash pe-2"></i><span>Delete</span></button>
                 </li><li class="d-flex justify-content-center"><button type="button" class="btn btn-outline-success btn-sm"><i class="fa far fa-user-edit pe-2"></i><span>Update</span></button>
                 </li>
                  
                  </ul>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "projects-table",
  data() {
    return {
      Student: [
        {
          img: "logo-spotify.svg",
          name: "Spotify",
          price: "$22,500",
          state: "working",
        },
        {
          img: "logo-spotify.svg",
          name: "Prenom",
          price: "$42,500",
          state: "Not working",
        },
        {
          img: "logo-spotify.svg",
          name: "Nom",
          price: "$42,500",
          state: "Not working",
        },
      ],
    };
  },
};
</script>
