<template>
  <div class="container">
    <h1>Интерполяция кубичного уравнения методом Лагранжа👀</h1>
    <div class="row justify-content-center">
      <div class="col-6 col-sm-4 col-md-2 col-lg-1 mb-2">
        <div class="form-floating">
          <input
            type="number"
            v-model.number="xzero"
            class="form-control"
            id="xzero"
          />
          <label for="xzero">x<sub>0</sub></label>
        </div>
      </div>
      <div class="col-6 col-sm-4 col-md-2 col-lg-1 mb-2">
        <div class="form-floating">
          <input
            type="number"
            v-model.number="yzero"
            class="form-control"
            id="yzero"
          />
          <label for="xzero">y<sub>0</sub></label>
        </div>
      </div>
      <div class="col-6 col-sm-4 col-md-2 col-lg-1 mb-2">
        <div class="form-floating">
          <input
            type="number"
            v-model.number="xone"
            class="form-control"
            id="xone"
          />
          <label for="xzero">x<sub>1</sub></label>
        </div>
      </div>
      <div class="col-6 col-sm-4 col-md-2 col-lg-1 mb-2">
        <div class="form-floating">
          <input
            type="number"
            v-model.number="yone"
            class="form-control"
            id="yone"
          />
          <label for="xzero">y<sub>1</sub></label>
        </div>
      </div>
      <div class="col-6 col-sm-4 col-md-2 col-lg-1 mb-2">
        <div class="form-floating">
          <input
            type="number"
            v-model.number="xtwo"
            class="form-control"
            id="xtwo"
          />
          <label for="xzero">x<sub>2</sub></label>
        </div>
      </div>
      <div class="col-6 col-sm-4 col-md-2 col-lg-1 mb-2">
        <div class="form-floating">
          <input
            type="number"
            v-model.number="ytwo"
            class="form-control"
            id="ytwo"
          />
          <label for="ytwo">y<sub>2</sub></label>
        </div>
      </div>
      <div class="col-6 col-sm-4 col-md-2 col-lg-1 mb-2">
        <div class="form-floating">
          <input
            type="number"
            v-model.number="xthree"
            class="form-control"
            id="xtwo"
          />
          <label for="xzero">x<sub>3</sub></label>
        </div>
      </div>
      <div class="col-6 col-sm-4 col-md-2 col-lg-1 mb-2">
        <div class="form-floating">
          <input
            type="number"
            v-model.number="ythree"
            class="form-control"
            id="ythree"
          />
          <label for="xzthree">y<sub>3</sub></label>
        </div>
      </div>
    </div>
    <div class="row justify-content-center mb-2">
      <div class="col-12" ref="x0"></div>
      <div class="col-12" ref="x1"></div>
      <div class="col-12" ref="x2"></div>
      <div class="col-12" ref="x3"></div>
    </div>
    <div class="row justify-content-center">
      <div class="col-6 col-sm-4 col-md-3 col-lg-2 mb-2">
        <table class="table table-bordered">
          <tbody>
            <tr>
              <th scope="row">x</th>
              <td>{{ xzero }}</td>
              <td>{{ xone }}</td>
              <td>{{ xtwo }}</td>
              <td>{{ xthree }}</td>
            </tr>
            <tr>
              <th scope="row">y</th>
              <td>{{ yzero }}</td>
              <td>{{ yone }}</td>
              <td>{{ ytwo }}</td>
              <td>{{ ythree }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <div class="row justify-content-center mb-2">
      <div class="col-12 mb-4">
        <div ref="exp1"></div>
      </div>
      <div class="col-12 mb-4">
        <div ref="exp2"></div>
      </div>
      <div class="col-12 mb-4">
        <div ref="exp3"></div>
      </div>
      <div class="col-12 mb-4">
        <div ref="exp4"></div>
      </div>
      <div class="col-12 mb-4">
        <div ref="exp5"></div>
      </div>
      <div class="col-12 mb-4">
        <div ref="exp6"></div>
      </div>
      <div class="col-6 col-sm-4 col-md-2 col-lg-1 mb-2">
        <div class="form-floating">
          <input
            type="number"
            v-model.number="xn"
            class="form-control"
            id="xn"
          />
          <label for="xn">x<sub>искомое</sub></label>
        </div>
      </div>
      <div class="col-12 mb-4">
        <div ref="exp7"></div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import "katex/dist/katex.min.css";
import katex from "katex";
export default {
  name: "App",
  data() {
    return {
      xzero: 0,
      yzero: 0,
      xone: 0,
      yone: 0,
      xtwo: 0,
      ytwo: 0,
      xthree: 0,
      ythree: 0,
      xn: 0,
    };
  },
  setup() {
    const x0 = ref(null);
    const x1 = ref(null);
    const x2 = ref(null);
    const x3 = ref(null);
    const exp1 = ref(null);
    const exp2 = ref(null);
    const exp3 = ref(null);
    const exp4 = ref(null);
    const exp5 = ref(null);
    const exp6 = ref(null);
    const exp7 = ref(null);
    return {
      exp1,
      exp2,
      exp3,
      exp4,
      exp5,
      exp6,
      exp7,
      x0,
      x1,
      x2,
      x3,
    };
  },
  mounted() {
    this.renderFExp();
  },
  updated() {
    this.renderFExp();
  },
  methods: {
    reduce(numer, denomin) {
      var gcd = function gcd(a, b) {
        return b ? gcd(b, a % b) : a;
      };
      return gcd(numer, denomin);
    },
    getCoef(n, d) {
      var ret = "";
      if (d == 0) {
        ret = `\\frac{${n}}{${d}}*`;
      } else {
        if (n % d == 0) {
          ret = `${n / d} *`;
        } else {
          var gcd = this.reduce(n, d);
          ret = `\\frac{${n / gcd}}{${d / gcd}} *`;
        }
      }
      return ret;
    },
    formatSigns(str) {
      return str
        .replaceAll("- -", "+")
        .replaceAll("- +", "-")
        .replaceAll("--", "+")
        .replaceAll("-+", "-")
        .replaceAll("+-", "-")
        .replaceAll("+ -", "-");
    },
    renderFExp() {
      katex.render(`f(x0 = ${this.xzero}) = ${this.yzero}`, this.x0, {
        throwOnError: false,
      });
      katex.render(`f(x1 = ${this.xone}) = ${this.yone}`, this.x1, {
        throwOnError: false,
      });
      katex.render(`f(x2 = ${this.xtwo}) = ${this.ytwo}`, this.x2, {
        throwOnError: false,
      });
      katex.render(`f(x3 = ${this.xthree}) = ${this.ythree}`, this.x3, {
        throwOnError: false,
      });

      katex.render(
        "\\huge L\\normalsize 2 \\LARGE (x) =  " +
          "\\frac{\\large(x - x \\small 1\\large)(x - x \\small 2\\large)(x - x \\small 3\\large)}{\\large(x\\small 0\\large - x \\small 1\\large)(x\\small 0\\large- x \\small 2\\large)(x\\small 0\\large- x \\small 3\\large)} \\large* y\\small 0\\large  + " +
          "\\frac{\\large(x - x \\small 0\\large)(x - x \\small 2\\large)(x - x \\small 3\\large)}{\\large(x\\small 1\\large - x \\small 0\\large)(x\\small 1\\large- x \\small 2\\large)(x\\small 1\\large - x \\small 3\\large)} \\large* y\\small 1\\large  + " +
          "\\frac{\\large(x - x \\small 0\\large)(x - x \\small 1\\large)(x - x \\small 3\\large)}{\\large(x\\small 2\\large - x \\small 0\\large)(x\\small 2\\large- x \\small 1\\large)(x\\small 2\\large- x \\small 3\\large)} \\large* y\\small 2\\large + " +
          "\\frac{\\large(x - x \\small 0\\large)(x - x \\small 1\\large)(x - x \\small 2\\large)}{\\large(x\\small 3\\large - x \\small 0\\large)(x\\small 3\\large- x \\small 1\\large)(x\\small 3\\large- x \\small 2\\large)} \\large* y\\small 3\\large",
        this.exp1,
        {
          throwOnError: false,
        }
      );
      var exp2str =
        ` =  ` +
        `\\frac{\\large(x - ${this.xone})(x - ${this.xtwo})(x - ${this.xthree})}{\\large(${this.xzero} - ${this.xone})(${this.xzero} -${this.xtwo})(${this.xzero} -${this.xthree})}\\normalsize *  ${this.yzero}  + ` +
        `\\frac{\\large(x - ${this.xzero})(x - ${this.xtwo})(x - ${this.xthree})}{\\large(${this.xone} - ${this.xzero})(${this.xone}- ${this.xtwo})(${this.xone}- ${this.xthree})} * ${this.yone}  + ` +
        `\\frac{\\large(x - ${this.xzero})(x - ${this.xone})(x - ${this.xthree})}{\\large(${this.xtwo} - ${this.xzero})(${this.xtwo}- ${this.xone})(${this.xtwo} - ${this.xthree})} *  ${this.ytwo} + ` +
        `\\frac{\\large(x - ${this.xzero})(x - ${this.xone})(x - ${this.xtwo})}{\\large(${this.xthree} - ${this.xzero})(${this.xthree}- ${this.xone})(${this.xthree} - ${this.xtwo})} *  ${this.ythree} = `;

      katex.render(this.formatSigns(exp2str), this.exp2, {
        throwOnError: false,
      });

      var num0_x3 = 1;
      var num0_x2 = -(this.xone + this.xtwo + this.xthree);
      var num0_x1 = -(
        -(this.xone + this.xtwo) * this.xthree -
        this.xone * this.xtwo
      );
      var num0_x0 = -this.xone * this.xtwo * this.xthree;
      var num0_denum =
        (this.xzero - this.xone) *
        (this.xzero - this.xtwo) *
        (this.xzero - this.xthree);
      var num0str = `x^{3} + ${num0_x2}x^{2} + ${num0_x1}x +${num0_x0}`;
      var num0c = this.yzero / num0_denum;

      var num1_x3 = 1;
      var num1_x2 = -(this.xzero + this.xtwo + this.xthree);
      var num1_x1 = -(
        -(this.xzero + this.xtwo) * this.xthree -
        this.xzero * this.xtwo
      );
      var num1_x0 = -this.xzero * this.xtwo * this.xthree;
      var num1_denum =
        (this.xone - this.xzero) *
        (this.xone - this.xtwo) *
        (this.xone - this.xthree);
      var num1str = `x^{3} + ${num1_x2}x^{2} + ${num1_x1}x +${num1_x0}`;
      var num1c = this.yone / num1_denum;

      var num2_x3 = 1;
      var num2_x2 = -(this.xone + this.xzero + this.xthree);
      var num2_x1 = -(
        -(this.xone + this.xzero) * this.xthree -
        this.xone * this.xzero
      );
      var num2_x0 = -this.xone * this.xzero * this.xthree;
      var num2_denum =
        (this.xtwo - this.xone) *
        (this.xtwo - this.xzero) *
        (this.xtwo - this.xthree);
      var num2str = `x^{3} + ${num2_x2}x^{2} + ${num2_x1}x +${num2_x0}`;
      var num2c = this.ytwo / num2_denum;

      var num3_x3 = 1;
      var num3_x2 = -(this.xone + this.xzero + this.xtwo);
      var num3_x1 = -(
        -(this.xone + this.xzero) * this.xtwo -
        this.xone * this.xzero
      );
      var num3_x0 = -this.xone * this.xzero * this.xtwo;
      var num3_denum =
        (this.xthree - this.xone) *
        (this.xthree - this.xzero) *
        (this.xthree - this.xtwo);
      var num3str = `x^{3} + ${num3_x2}x^{2} + ${num3_x1}x +${num3_x0}`;
      var num3c = this.ythree / num3_denum;

      var total_x3 = num0c + num1c + num2c + num3c;
      var total_x2 =
        num0c * num0_x2 + num1c * num1_x2 + num2c * num2_x2 + num3c * num3_x2;
      var total_x1 =
        num0c * num0_x1 + num1c * num1_x1 + num2c * num2_x1 + num3c * num3_x1;
      var total_x0 =
        num0c * num0_x0 + num1c * num1_x0 + num2c * num2_x0 + num3c * num3_x0;

      var exp3str =
        ` =  ` +
        `\\frac{\\large ${num0str}}{\\large ${num0_denum}}\\normalsize *  ${this.yzero}  + ` +
        `\\frac{\\large ${num1str}}{\\large ${num1_denum}} * ${this.yone}  + ` +
        `\\frac{\\large ${num2str}}{\\large ${num2_denum}} *  ${this.ytwo} =` +
        `\\frac{\\large ${num3str}}{\\large ${num3_denum}} *  ${this.ythree} =`;
      katex.render(this.formatSigns(exp3str), this.exp3, {
        throwOnError: false,
      });

      var exp4str =
        `\\large = ` +
        `${this.getCoef(this.yzero, num0_denum)} (${num0str}) + ` +
        `${this.getCoef(this.yone, num1_denum)} (${num1str}) + ` +
        `${this.getCoef(this.ytwo, num2_denum)} (${num2str}) + ` +
        `${this.getCoef(this.ythree, num3_denum)} (${num3str}) = `;
      katex.render(this.formatSigns(exp4str), this.exp4, {
        throwOnError: false,
      });

      var exp5str =
        `\\large = ` +
        `${this.getCoef(this.yzero, num0_denum)}x^{3}+ ${this.getCoef(
          this.yzero * num0_x2,
          num0_denum
        )}x^{2} + ${this.getCoef(
          this.yzero * num0_x1,
          num0_denum
        )}x +${this.getCoef(this.yzero * num0_x0, num0_denum)} +` +
        `${this.getCoef(this.yone, num1_denum)}x^{3}+${this.getCoef(
          this.yzone * num1_x1,
          num1_denum
        )}x^{2} + ${this.getCoef(
          this.yone * num1_x2,
          num1_denum
        )}x +${this.getCoef(this.yone * num1_x0, num1_denum)} +` +
        `${this.getCoef(this.ytwo, num2_denum)}x^{3}+${this.getCoef(
          this.ytwo * num2_x2,
          num2_denum
        )}x^{2} + ${this.getCoef(
          this.ytwo * num2_x1,
          num2_denum
        )}x +${this.getCoef(this.ytwo * num2_x0, num2_denum)} +` +
        `${this.getCoef(this.ythree * num3_x3, num3_denum)}x^{3}+${this.getCoef(
          this.ythree * num3_x2,
          num3_denum
        )}x^{2} + ${this.getCoef(
          this.ythree * num3_x1,
          num3_denum
        )}x +${this.getCoef(this.ythree * num3_x0, num3_denum)}`;
      katex.render(this.formatSigns(exp5str), this.exp5, {
        throwOnError: false,
      });

      var exp6str =
        `\\large = ` +
        `${total_x3}x^{3}  +${total_x2}x^{2} + ${total_x1}x +${total_x0};`;
      katex.render(this.formatSigns(exp6str), this.exp6, {
        throwOnError: false,
      });

      var exp7str = `\\large f(x = ${this.xn}) = ${
        total_x3 * (this.xn * this.xn * this.xn) +
        total_x2 * (this.xn * this.xn) +
        total_x1 * this.xn +
        total_x0
      };`;
      katex.render(this.formatSigns(exp7str), this.exp7, {
        throwOnError: false,
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
