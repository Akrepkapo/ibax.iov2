<template>
  <div class="team">
    <div id="technical" class="parallax-container--over">
      <section
        id="parallax-container--top"
        class="about-us-hero"
        data-menu-theme="dark"
      >
        <el-row type="flex" justify="center">
          <el-col :xs="24" :sm="22" :md="20" :lg="18">
            <!-- <strong class="block-title lg">Our mission</strong> -->
            <h1 class="title-h2 wow fadeInUp">
              {{ $t('resource.technical') }}
            </h1>
            <ul class="customers-list">
              <li v-for="(item, index) in arrPatter" :key="index">
                <i :class="item.icon"></i>
                <img :src="item.img" class="attachment-medium wow fadeInUp" />
              </li>
            </ul>
            <a
              href="https://github.com/IBAX-io/go-ibax/issues"
              target="_blank"
              class="home-new-bottom link wow fadeInUp"
            >
              <span>{{ $t('resource.know') }}</span>
              <i class="el-icon-right"></i>
            </a>
          </el-col>
        </el-row>
      </section>
    </div>
    <div v-show="!isMobile" ref="parallax" class="team-middle"></div>
    <div
      ref="composed"
      class="team-fixed"
      :style="{ position: isMobile ? 'static' : 'fixed' }"
    >
      <el-row type="flex" justify="center">
        <el-col :xs="24" :sm="22" :md="20" :lg="18" class="el-row-wrap">
          <div class="header wow fadeInUp">
            <h3>Who we are</h3>
          </div>
          <div class="team-fixed-content">
            <p class="wow fadeInUp">
              {{ $t('resource.composed') }}
            </p>
            <p class="wow fadeInUp">
              {{ $t('resource.needs') }}
            </p>
          </div>
          <div class="team-fixed-box">
            <el-row type="flex" justify="space-between">
              <el-col :xs="23" :lg="7">
                <div class="inner wow fadeInUp">
                  <strong>{{ $t('resourse.hundreds') }}</strong>
                  <div>{{ $t('resourse.r') }}</div>
                </div>
              </el-col>
              <el-col :xs="23" :lg="7">
                <div class="inner wow fadeInUp">
                  <strong>{{ $t('resourse.chain') }}</strong>
                  <div>{{ $t('resourse.underlying') }}</div>
                </div>
              </el-col>
              <el-col :xs="23" :lg="7">
                <div class="inner wow fadeInUp">
                  <strong>3000</strong>
                  <div>TPS</div>
                </div>
              </el-col>
            </el-row>
          </div>
          <div class="team-fixed-box">
            <el-row type="flex" justify="space-between">
              <el-col :xs="23" :lg="7">
                <div class="inner wow fadeInUp">
                  <strong>{{ $t('resourse.items') }}</strong>
                  <div>{{ $t('resourse.leading') }}</div>
                </div>
              </el-col>
              <el-col :xs="23" :lg="7">
                <div class="inner wow fadeInUp">
                  <strong>{{ $t('resourse.application') }}</strong>
                  <div>{{ $t('resourse.system') }}</div>
                </div>
              </el-col>
              <el-col :xs="23" :lg="7">
                <div class="inner wow fadeInUp">
                  <strong>{{ $t('resourse.machine') }}</strong>
                  <div>{{ $t('resourse.languages') }}</div>
                </div>
              </el-col>
            </el-row>
          </div>
        </el-col>
      </el-row>
    </div>
    <div class="team-rate" style="display: none">
      <div class="team-rate-icon wow fadeInUp">
        <i class="iconfont el-GitHub"></i>
      </div>
      <h3 class="wow fadeInUp">{{ $t('resourse.still') }}</h3>
      <div class="team-loop">
        <div v-if="iconList.length" class="team-loop-content">
          <client-only>
            <vue-seamless-scroll
              :data="iconList"
              :class-option="optionLeft"
              class="team-loop-content-scroll"
            >
              <ul class="ul-scoll">
                <li v-for="item in iconList" :key="item.id">
                  <a :href="item.html_url">
                    <div class="team-loop-content-head">
                      <div class="team-loop-content-head-img">
                        <img :src="item.user.avatar_url" alt="avatar" />
                      </div>
                      <span class="team-loop-content-head-text">{{
                        item.user.login
                      }}</span>
                      <div class="team-loop-content-head-right">
                        <i class="iconfont el-GitHub"></i>
                      </div>
                    </div>
                    <div class="team-loop-content-title">{{ item.title }}</div>
                    <div v-if="item.body" class="team-loop-content-body">
                      {{ item.body }}
                    </div>
                  </a>
                </li>
              </ul>
            </vue-seamless-scroll>
          </client-only>
        </div>
        <div v-else class="team-loop-no">{{ $t('resourse.no') }}</div>
      </div>
      <div>
        <a
          href="https://github.com/orgs/IBAX-io/people"
          target="_blank"
          class="btn btn-primary wow fadeInUp"
          >{{ $t('resourse.view') }}</a
        >
      </div>
    </div>
    <div class="team-leader">
      <div class="team-leader-top">
        <h2 class="h1 wow fadeInUp">{{ $t('resourse.person') }}</h2>
        <p class="wow fadeInUp">
          {{ $t('resourse.charge') }}
        </p>
      </div>
      <div class="team-slick">
        <div class="team-slick-btn" style="display: none">
          <button class="team-slick-btn-item" @click="handleShowPre">
            <i class="el-icon-arrow-left"></i>
          </button>
          <button class="team-slick-btn-item" @click="handleShowNext">
            <i class="el-icon-arrow-right"></i>
          </button>
        </div>
        <el-row type="flex" justify="center">
          <el-col :xs="23" :sm="22" :md="20" :lg="18">
            <client-only>
              <vue-slick-carousel
                ref="carousel"
                :slides-to-show="4"
                :focus-on-select="true"
                @afterChange="handleAfterChange"
              >
                <a
                  v-for="(item, index) in arrPeople"
                  :key="index"
                  class="team-slick-item"
                >
                  <div class="team-slick-item-img">
                    <img :src="item.img" :alt="item.img" />
                    <div>{{ item.name }}</div>
                    <div>{{ item.position }}</div>
                  </div>
                </a>
              </vue-slick-carousel>
            </client-only>
          </el-col>
        </el-row>
      </div>
    </div>
    <div class="team-bod">
      <div class="container">
        <h3 class="wow fadeInUp">{{ $t('resourse.senior') }}</h3>
        <ul class="investors-bod-list">
          <li v-for="item in arrBod" :key="item.alt">
            <div class="avatar-wrap wow fadeInUp">
              <img :src="item.img" class="attachment-full" :alt="item.alt" />
            </div>
            <div class="info-wrap wow fadeInUp">
              <strong class="name">{{ item.name }}</strong>
              <strong class="post">{{ $t(item.introduce) }}</strong>
            </div>
          </li>
        </ul>
      </div>
    </div>
    <div id="introduce" class="team-serving">
      <el-row type="flex" justify="center">
        <el-col :xs="23" :sm="22" :md="20" :lg="18">
          <div class="team-serving-header wow fadeInUp">
            <h3>{{ $t('resourse.from') }}</h3>
          </div>
          <el-row type="flex" justify="center" style="flex-flow: wrap">
            <el-col
              v-for="(item, index) in arrTeam"
              :key="index"
              :xs="23"
              :sm="12"
              :md="8"
              :lg="7"
            >
              <div class="team-serving-content">
                <div class="team-serving-content-img">
                  <img
                    :src="item.img"
                    class="attachment-medium wow fadeInUp"
                    alt="item.name"
                  />
                </div>
                <strong class="place wow fadeInUp">{{ item.name }}</strong>
                <div class="team-serving-content-text wow fadeInUp">
                  {{ item.label }}<br />
                  {{ $t(item.des) }}
                </div>
              </div>
            </el-col>
          </el-row>
        </el-col>
      </el-row>
    </div>
  </div>
</template>
<script>
const ceo1 = require('../../assets/images/avatars/ceo-1.png');
const ceo2 = require('../../assets/images/avatars/ceo-2.png');
const ceo3 = require('../../assets/images/avatars/ceo-3.png');
const ceo4 = require('../../assets/images/avatars/ceo-4.png');
const adviser1 = require('../../assets/images/avatars/adviser-1.png');
const adviser2 = require('../../assets/images/avatars/adviser-2.png');
const adviser3 = require('../../assets/images/avatars/adviser-3.png');
const member1 = require('../../assets/images/avatars/member-1.png');
const member2 = require('../../assets/images/avatars/member-2.png');
const member3 = require('../../assets/images/avatars/member-3.png');
const member4 = require('../../assets/images/avatars/member-4.jpg');
const member5 = require('../../assets/images/avatars/member-5.png');
const member6 = require('../../assets/images/avatars/member-6.png');
const member7 = require('../../assets/images/avatars/member-7.png');
const member8 = require('../../assets/images/avatars/member-8.png');
const jwhite = require('../../assets/images/jwhite.png');
export default {
  props: {},
  data() {
    return {
      arrTeam: [
        {
          img: member1,
          name: 'UK',
          label: 'Clifford G.Gordon',
          des: 'resourse.developer'
        },
        {
          img: member2,
          name: 'Singapore',
          label: 'RenRan Chen',
          des: 'resourse.designer'
        },
        {
          img: member3,
          name: 'Australia',
          label: 'Jane Oakley',
          des: 'resourse.soon'
        },
        {
          img: member4,
          name: 'Singapore',
          label: 'Chen Ren',
          des: 'resourse.joined'
        },
        {
          img: member5,
          name: 'US',
          label: 'Harold Aziz',
          des: 'resourse.responsible'
        },
        {
          img: member6,
          name: 'US',
          label: 'Nathan Conley',
          des: 'resourse.hum'
        },
        {
          img: member7,
          name: 'Italy',
          label: 'Alberto Angelo',
          des: 'resourse.our'
        },
        {
          img: member8,
          name: 'US',
          label: 'Rebecca Bourquin',
          des: 'resourse.administrative'
        }
      ],
      arrBod: [
        {
          img: adviser1,
          alt: 'adviser-1',
          name: 'David Morrison',
          introduce: 'resourse.professor'
        },
        {
          img: adviser2,
          alt: 'adviser-2',
          name: 'Rakib Sajid',
          introduce: 'resourse.doctor'
        },
        {
          img: adviser3,
          alt: 'adviser-3',
          name: 'Priscilla Wang ',
          introduce: 'resourse.affairs'
        }
      ],
      arrPatter: [
        {
          icon: 'iconfont el-pusher_logo'
        },
        {
          img: jwhite
        }
      ],
      arrPeople: [
        {
          img: ceo1,
          name: 'Stuart Nichols',
          position: 'CEO'
        },
        {
          img: ceo2,
          name: 'Alan McIvor',
          position: 'COO'
        },
        {
          img: ceo3,
          name: 'Gianluca Matrullo',
          position: 'CMO'
        },
        {
          img: ceo4,
          name: 'Simon Hemmrich',
          position: 'Senior Consultant'
        }
      ],
      parallax: '',
      fixed: '',
      wScroll: 0,
      container: 0,
      domGlobal: '',
      optionLeft: {
        width: '100%',
        step: 1,
        // limitMoveNum: 11,
        hoverStop: true,
        direction: 2, // 0-dwon 1-up 2-left 3-right
        openWatch: true,
        singleHeight: 0,
        singleWidth: 0,
        waitTime: 10
      },
      iconList: [],
      settings: {
        dots: true,
        infinite: false,
        speed: 500,
        slidesToShow: 4,
        slidesToScroll: 1,
        initialSlide: 0,
        responsive: [
          {
            breakpoint: 1024,
            settings: {
              slidesToShow: 4,
              slidesToScroll: 4,
              infinite: true,
              dots: true
            }
          },
          {
            breakpoint: 824,
            settings: {
              slidesToShow: 3,
              slidesToScroll: 3,
              infinite: true,
              dots: true
            }
          },
          {
            breakpoint: 600,
            settings: {
              slidesToShow: 2,
              slidesToScroll: 2,
              initialSlide: 2
            }
          },
          {
            breakpoint: 480,
            settings: {
              slidesToShow: 1,
              slidesToScroll: 1
            }
          }
        ]
      },
      /*  settings: {
        variableWidth: true,
        dots: true,
        infinite: true,
        centerMode: true,
        speed: 500,
        arrows: true,
        slidesToShow: 4,
        slidesToScroll: 4,
        swipe: true,
        centerPadding: '20px',
        swipeToSlide: true
      }, */
      obj: {
        dots: true,
        infinite: false,
        speed: 500,
        slidesToShow: 4,
        slidesToScroll: 4,
        initialSlide: 0,
        responsive: [
          {
            breakpoint: 1024,
            settings: {
              slidesToShow: 3,
              slidesToScroll: 3,
              infinite: true,
              dots: true
            }
          },
          {
            breakpoint: 600,
            settings: {
              slidesToShow: 2,
              slidesToScroll: 2,
              initialSlide: 2
            }
          },
          {
            breakpoint: 480,
            settings: {
              slidesToShow: 1,
              slidesToScroll: 1
            }
          }
        ]
      }
    };
  },
  head() {
    return {
      title: `Team | IBAX Network`,
      meta: [
        {
          hid: 'keywords',
          name: 'keywords',
          content:
            'IBAX, Blockchain, CryptoCurrency, Bitcoin, Cross-Chain, Crypto, DeFi, Dapps,Blockchaintechnology, Corelayertechnology, Decentralizedapplication,Distributedledger, IBAXAMA,BlockChain,BaaS,DAO,Token,contract,LowCode,Reward'
        },
        {
          hid: 'description',
          name: 'description',
          content: `Committed To Changing Society With Blockchain Technology`
        },
        {
          hid: 'og:url',
          property: 'og:url',
          content: `${this.baseUrl}${this.$route.path}`
        },
        {
          hid: 'twitter:url',
          property: 'twitter:url',
          content: `${this.baseUrl}${this.$route.path}`
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: `Evnets | IBAX Network`
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: `Committed To Changing Society With Blockchain Technology`
        },
        {
          hid: 'twitter:title',
          property: 'twitter:title',
          content: `Evnets | IBAX Network`
        },
        {
          hid: 'twitter:description',
          property: 'twitter:description',
          content: `Committed To Changing Society With Blockchain Technology`
        }
      ]
    };
  },
  computed: {},
  watch: {},
  created() {
    // this.handleGethubIssues();
  },
  mounted() {
    if (this.isMobile) {
      this.settings.slidesToShow = 1;
    } else {
      this.settings.slidesToShow = 3;
    }
    this.$nextTick(() => {
      this.domGlobal = document.getElementById('global').firstChild;
      this.domHeaderTop = document.getElementById('headerTop');
      const obj = { headerColor: '#274235', color: '#fff' };
      this.$store.commit('handleChangeColor', obj);
      this.$store.commit('handleIsTop', true);
      this.$store.commit('handleIsFixed', false);
      this.$store.commit('handleChangeClass', 'subMenu--horizontal');
      const wow = new this.WOW({
        boxClass: 'wow',
        animateClass: 'animated',
        scrollContainer: '.el-scrollbar__wrap',
        offset: 0,
        mobile: true,
        live: false
      });
      wow.init();
      this.composed = this.$refs.composed;
      this.parallax = this.$refs.parallax;
      this.container = this.$refs.container;
      this.composedtHeight = this.composed.offsetHeight;
      this.parallax.style.height = this.composedtHeight + 'px';
    });
    this.domGlobal.addEventListener('scroll', this.handleTeamScroll, true);
  },
  destroyed() {
    this.domGlobal.removeEventListener('scroll', this.handleTeamScroll, true);
  },
  methods: {
    handleTeamScroll() {
      const scrollTop = this.domGlobal.scrollTop;
      if (document.getElementById('headerTop')) {
        const topHeight = document.getElementById('headerTop').offsetTop;
        const isFixed = scrollTop > topHeight;
        this.$store.commit('handleIsFixed', isFixed);
      }
      this.numTechnical = document
        .getElementById('technical')
        .getBoundingClientRect().bottom;
      if (!this.isMobile) {
        this.composedtHeight = this.composed.offsetHeight;
        this.parallax.style.height = this.composedtHeight + 'px';

        if (this.numTechnical <= 0) {
          this.parallax.style.visibility = 'hidden';
          this.parallax.style.height = '0';
          this.composed.style.position = 'static';
        } else {
          this.parallax.style.visibility = 'visible';
          this.parallax.style.height = this.composedtHeight + 'px';
          this.composed.style.position = 'fixed';
        }
      }
      this.numIntroduce = document
        .getElementById('introduce')
        .getBoundingClientRect().top;
      if (this.numTechnical <= 0 && this.numIntroduce > 0) {
        const obj = { headerColor: '#fff', color: '#37383c' };
        this.$store.commit('handleChangeColor', obj);
        this.$store.commit('handleChangeClass', 'news--horizontal');
        this.$store.commit('handleIsTop', false);
      } else if (this.numIntroduce <= 0) {
        const obj = { headerColor: '#274235', color: '#fff' };
        this.$store.commit('handleChangeColor', obj);
        this.$store.commit('handleChangeClass', 'subMenu--horizontal');
        this.$store.commit('handleIsTop', true);
      } else {
        const obj = { headerColor: '#274235', color: '#fff' };
        this.$store.commit('handleChangeColor', obj);
        this.$store.commit('handleChangeClass', 'subMenu--horizontal');
        this.$store.commit('handleIsTop', true);
      }
    },
    handleAfterChange(e) {
      console.log(e);
    },
    handleShowPre() {
      console.log(this.$refs.carousel);
      this.$refs.carousel.prev();
    },
    handleShowNext(e) {
      console.log(this.$refs.carousel);
      this.$refs.carousel.next();
    }
  }
};
</script>
