<!-- eslint-disable vue/valid-v-for -->
<template>
  <div class="container-xl">
    <div class="container text-center">
      <div class="header">
        <img
          src="\public\img\logomju.png"
          style="width: 70px; hight: 70px"
          alt=""
        />
        <h1 style="font-size: 150%">คำร้องขอย้ายสาขาวิชาต่างคณะ</h1>
      </div>
    </div>
    <br />
    <div class="col align-self-start">
      วันที่เขียน
      <input class="form-control" type="date" v-model="person.date" /><br />
      เรียน คณบดีคณะ
      <input
        class="form-control"
        type="text"
        placeholder="ชื่อคณะ"
        aria-label="default input example"
        v-model="person.facultyt"
      />
    </div>
    <div class="container text-center">
      <div class="row">
        <div class="col-sm">
          ข้าพเจ้า
          <select
            name="selecttitleF"
            class="form-select"
            aria-label="Default select example"
            v-model="person.title"
          >
            <option value="นาย">นาย</option>
            <option value="นาง">นาง</option>
            <option value="นางสาว">นางสาว</option>
          </select>
        </div>
        <div class="col-sm">
          ชื่อ
          <input
            type="text"
            class="form-control"
            placeholder="First name"
            aria-label="First name"
            v-model="person.fname"
          />
        </div>
        <div class="col-sm">
          นามสกุล
          <input
            type="text"
            class="form-control"
            placeholder="Last name"
            aria-label="Last name"
            v-model="person.lname"
          />
        </div>
      </div>
      <div class="row">
        <div class="col">
          รหัสนักศึกษา
          <input
            type="text"
            class="form-control"
            placeholder="StudentID"
            aria-label="StudentID"
            v-model="person.stdId"
          />
        </div>
        <div class="col">
          เบอร์โทร
          <input
            type="text"
            class="form-control"
            placeholder="Phonenumber"
            aria-label="Phonenumber"
            v-model="person.numphon"
          />
        </div>
      </div>
      <div class="row">
        <div class="col">
          หลักสูตร
          <select
            name="seleccourse"
            class="form-select"
            aria-label="Default select example"
            v-model="person.course"
          >
            <option value="4 - 5 ปี">4 - 5 ปี</option>
            <option value="4 ปีเทียบเข้าเรียน (2ปี)">
              4 ปีเทียบเข้าเรียน (2ปี)
            </option>
          </select>
        </div>
        <div class="col">
          สาขา
          <input
            type="text"
            class="form-control"
            placeholder="Major"
            aria-label="Major"
            v-model="person.major"
          />
        </div>
        <div class="col">
          คณะ<input
            type="text"
            class="form-control"
            placeholder="Faculty"
            aria-label="Faculty"
            v-model="person.facultystd"
          />
        </div>
      </div>
      <div class="row">
        <div class="col align-self-start">
          มีความประสงค์จะขอโอนย้ายไปสาขาวิชา<input
            type="text"
            class="form-control"
            placeholder="To"
            aria-label="To"
            v-model="person.to"
          />
        </div>
      </div>
      <div class="row">
        <div class="col align-self-start">
          เนื่องจาก<input
            type="text"
            class="form-control"
            placeholder="Reason"
            aria-label="Reason"
            style="height: 100px"
            v-model="person.reason"
          />
        </div>
      </div>
    </div>
    <div class="col-md-12 text-center">
      <br />
      <button type="submit" class="btn btn-primary" @click.prevent="addform">
        ส่ง
      </button>
    </div>
    <br />

    <div class="card">
      <div class="container text-center">รวมรายชื่อผู้ส่งแบบฟอร์ม</div>
      <div class="card-body">
        <table class="table">
          <thead>
            <tr>
              <th scope="col">ชื่อ-นามสกุล</th>
              <th scope="col">คณะ</th>
              <th scope="col">ต้องการย้ายไปสาขา</th>
              <th scope="col">วันที่เขียน</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(person, index) in Arrayperson" :key="index">
              <td>{{ person.title }}{{ person.fname }} {{ person.lname }}</td>
              <td>{{ person.facultystd }}</td>
              <td>{{ person.to }}</td>
              <td>{{ person.date }}</td>
              <tfoot>
                <button
                  type="button"
                  class="btn btn-danger"
                  @click="deleteform(index)"
                >
                  ลบ
                </button>
              </tfoot>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      person: {
        date: null,
        facultyt: "",
        title: "",
        fname: "",
        lname: "",
        stdId: "",
        numphon: "",
        course: "",
        major: "",
        facultystd: "",
        to: "",
        reason: "",
      },
      Arrayperson: [],
    };
  },
  methods: {
    addform() {
      alert("ยืนยันการส่งแบบฟอร์ม");
      this.Arrayperson.push(this.person);

      this.person = {
        date: null,
        facultyt: "",
        title: "",
        fname: "",
        lname: "",
        stdId: "",
        numphon: "",
        course: "",
        major: "",
        facultystd: "",
        to: "",
        reason: "",
      };
    },
    deleteform(id) {
      alert("ยืนยันการลบแบบฟอร์ม");
      this.Arrayperson.splice(id, 1);
    },
  },
  prop: {
    fname: {
      type: String,
      required: true,
    },
    lname: {
      type: String,
      required: true,
    },
    facultyt: {
      type: String,
      required: true,
    },
    major: {
      type: String,
      required: true,
    },
    facultystd: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.header {
  display: flex;
  align-content: center;
  justify-content: center;
}
.header img {
  flex-grow: 1;
}
.header h1 {
  flex-grow: 4;
}
</style>
