<template>
  <div id="navbar">
    <b-navbar toggleable="lg" type="dark" variant="dark" sticky>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-navbar-brand href="/">
        <img
          src="../assets/icon.png"
          class="d-inline-block align-top ml-2"
          width="30rem"
          alt="logo"
        />
        DFA-ATM
      </b-navbar-brand>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item href="/">หน้าแรก</b-nav-item>

          <b-nav-item v-b-modal.about>คำแนะนำการใช้งาน</b-nav-item>
          <b-modal id="about" centered title="คำแนะนำการใช้งาน">
            <ol>
              <li>เสียบบัตรATM</li>
              <li>กรอกรหัสผ่าน '123' จากนั้นกดยืนยัน</li>
              <li>กรอกจำนวนเงินที่ต้องการถอน จากนั้นกดยืนยัน</li>
              <li>รับเงินและรับบัตรคืน</li>
              <p></p>
              <span>*กรณีกรอกรหัสผ่านผิด</span>
              <p>ต้องทำการกดปุ่มยืนยันจากนั้นกรอกรหัสผ่านใหม่อีกครั้ง</p>
              <p></p>
              <span>**กรณีระบุเงินที่ต้องการถอนผิด</span>
              <p>ต้องทำการกดปุ่มยืนยันจากนั้นระบุจำนวนเงินใหม่อีกครั้ง</p>
              <p></p>
              <span
                >***ปุ่มแก้ไข สามารถเคลียร์ข้อมูลใน input
                เพื่อกรอกใหม่ได้อีกครั้งสามารถใช้ได้เมื่อต้องการแก้ไขรหัสผ่านและจำนวนเงินที่ต้องการถอน</span
              >
              <p></p>
              <span
                >****ปุ่มยกเลิก จะทำการยกเลิกการทำรายการทั้งหมดไม่ว่าจะอยู่ใน
                state ไหน จากนั้นจะทำการคืนบัตร ATM ออกมา</span
              >
              <p></p>
              <span
                >*****ปุ่มReset จะทำการ Reset state
                ทั้งหมดและกลับไปเริ่มทำรายการถอนใหม่</span
              >
              <p></p>
              <span
                >*****ปุ่ม เปิด/ปิด เพลง จะทำการ เปิด/ปิด เพลงในเว็บ</span
              >
            </ol>
          </b-modal>

          <b-nav-item v-b-modal.atmdfa>รูปDFA</b-nav-item>
          <b-modal id="atmdfa" size="lg" centered title="รูปDFA">
            <v-img :src="atmdfa"></v-img>
          </b-modal>

          <b-nav-item v-b-modal.member>สมาชิก</b-nav-item>
          <b-modal id="member" centered title="สมาชิก">
            <ol>
              <li>นายชญานิน บัวสละ รหัสนักศึกษา 62015021</li>
              <li>นายณัฐภูมิ ล้อมเขตร รหัสนักศึกษา 62015038</li>
              <li>นายทรงวุฒิ นักร้อง รหัสนักศึกษา 62015044</li>
              <li>นายธนธัช อัศวรัตนากร รหัสนักศึกษา 62015048</li>
              <li>นายเสกสรรค์ ทองอ่อน รหัสนักศึกษา 62015123</li>
              <li>นายอรรถพล ตันติวัฒนะผล รหัสนักศึกษา 62015131</li>
            </ol>
          </b-modal>
        </b-navbar-nav>
      </b-collapse>

      <b-navbar-nav class="ml-auto">
        <b-button
          variant="success"
          size="sm"
          type="submit"
          @click="musicControle_Action()"
        >
          {{ musicControle_Status }}</b-button
        >
      </b-navbar-nav>

      <b-navbar-nav class="ml-auto" >
        <b-button variant="danger" style="margin-left: 15px;" size="sm" type="submit" v-on:click="reset"
          >RESET</b-button
        >
      </b-navbar-nav>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      atmdfa: require('/src/assets/atmdfa.png'),
    }
  },
  props: {
    reset: {
      type: Function,
    },
    musicControle_Status: {
      type: String,
    },
    musicControle_Action: {
      type: Function,
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Prompt&display=swap');

#navbar {
  font-family: 'Prompt', sans-serif;
  width: 100%;
  position: fixed;
  z-index: 10;
}

ol {
  padding-left: 15px;
}

.modal {
  font-family: 'Prompt', sans-serif;
}
</style>
