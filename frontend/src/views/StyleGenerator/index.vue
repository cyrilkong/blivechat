<template>
  <el-row :gutter="20">
    <el-col :span="12">
      <el-form label-width="150px" size="mini">
        <h3>{{$t('stylegen.outlines')}}</h3>
        <el-form-item :label="$t('stylegen.showOutlines')">
          <el-switch v-model="form.showOutlines"></el-switch>
        </el-form-item>
        <el-form-item :label="$t('stylegen.outlineSize')">
          <el-input v-model.number="form.outlineSize" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.outlineColor')">
          <el-color-picker v-model="form.outlineColor"></el-color-picker>
        </el-form-item>

        <h3>{{$t('stylegen.avatars')}}</h3>
        <el-form-item :label="$t('stylegen.showAvatars')">
          <el-switch v-model="form.showAvatars"></el-switch>
        </el-form-item>
        <el-form-item :label="$t('stylegen.avatarSize')">
          <el-input v-model.number="form.avatarSize" type="number" min="0"></el-input>
        </el-form-item>

        <h3>{{$t('stylegen.userNames')}}</h3>
        <el-form-item :label="$t('stylegen.showUserNames')">
          <el-switch v-model="form.showUserNames"></el-switch>
        </el-form-item>
        <el-form-item :label="$t('stylegen.font')">
          <el-autocomplete v-model="form.userNameFont" :fetch-suggestions="getFontSuggestions"></el-autocomplete>
        </el-form-item>
        <el-form-item :label="$t('stylegen.fontSize')">
          <el-input v-model.number="form.userNameFontSize" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.lineHeight')">
          <el-input v-model.number="form.userNameLineHeight" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.normalColor')">
          <el-color-picker v-model="form.userNameColor"></el-color-picker>
        </el-form-item>
        <el-form-item :label="$t('stylegen.ownerColor')">
          <el-color-picker v-model="form.ownerUserNameColor"></el-color-picker>
        </el-form-item>
        <el-form-item :label="$t('stylegen.moderatorColor')">
          <el-color-picker v-model="form.moderatorUserNameColor"></el-color-picker>
        </el-form-item>
        <el-form-item :label="$t('stylegen.memberColor')">
          <el-color-picker v-model="form.memberUserNameColor"></el-color-picker>
        </el-form-item>
        <el-form-item :label="$t('stylegen.showBadges')">
          <el-switch v-model="form.showBadges"></el-switch>
        </el-form-item>
        <el-form-item :label="$t('stylegen.showColon')">
          <el-switch v-model="form.showColon"></el-switch>
        </el-form-item>

        <h3>{{$t('stylegen.messages')}}</h3>
        <el-form-item :label="$t('stylegen.font')">
          <el-autocomplete v-model="form.messageFont" :fetch-suggestions="getFontSuggestions"></el-autocomplete>
        </el-form-item>
        <el-form-item :label="$t('stylegen.fontSize')">
          <el-input v-model.number="form.messageFontSize" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.lineHeight')">
          <el-input v-model.number="form.messageLineHeight" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.color')">
          <el-color-picker v-model="form.messageColor"></el-color-picker>
        </el-form-item>
        <el-form-item :label="$t('stylegen.onNewLine')">
          <el-switch v-model="form.messageOnNewLine"></el-switch>
        </el-form-item>

        <h3>{{$t('stylegen.time')}}</h3>
        <el-form-item :label="$t('stylegen.showTime')">
          <el-switch v-model="form.showTime"></el-switch>
        </el-form-item>
        <el-form-item :label="$t('stylegen.font')">
          <el-autocomplete v-model="form.timeFont" :fetch-suggestions="getFontSuggestions"></el-autocomplete>
        </el-form-item>
        <el-form-item :label="$t('stylegen.fontSize')">
          <el-input v-model.number="form.timeFontSize" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.lineHeight')">
          <el-input v-model.number="form.timeLineHeight" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.color')">
          <el-color-picker v-model="form.timeColor"></el-color-picker>
        </el-form-item>

        <h3>{{$t('stylegen.backgrounds')}}</h3>
        <el-form-item :label="$t('stylegen.bgColor')">
          <el-color-picker v-model="form.bgColor" show-alpha></el-color-picker>
        </el-form-item>
        <el-form-item :label="$t('stylegen.useBarsInsteadOfBg')">
          <el-switch v-model="form.useBarsInsteadOfBg"></el-switch>
        </el-form-item>
        <el-form-item :label="$t('stylegen.messageBgColor')">
          <el-color-picker v-model="form.messageBgColor" show-alpha></el-color-picker>
        </el-form-item>
        <el-form-item :label="$t('stylegen.ownerMessageBgColor')">
          <el-color-picker v-model="form.ownerMessageBgColor" show-alpha></el-color-picker>
        </el-form-item>
        <el-form-item :label="$t('stylegen.moderatorMessageBgColor')">
          <el-color-picker v-model="form.moderatorMessageBgColor" show-alpha></el-color-picker>
        </el-form-item>
        <el-form-item :label="$t('stylegen.memberMessageBgColor')">
          <el-color-picker v-model="form.memberMessageBgColor" show-alpha></el-color-picker>
        </el-form-item>

        <h3>{{$t('stylegen.scAndNewMember')}}</h3>
        <el-form-item :label="$t('stylegen.firstLineFont')">
          <el-autocomplete v-model="form.firstLineFont" :fetch-suggestions="getFontSuggestions"></el-autocomplete>
        </el-form-item>
        <el-form-item :label="$t('stylegen.firstLineFontSize')">
          <el-input v-model.number="form.firstLineFontSize" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.firstLineLineHeight')">
          <el-input v-model.number="form.firstLineLineHeight" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.firstLineColor')">
          <el-color-picker v-model="form.firstLineColor"></el-color-picker>
        </el-form-item>
        <el-form-item :label="$t('stylegen.secondLineFont')">
          <el-autocomplete v-model="form.secondLineFont" :fetch-suggestions="getFontSuggestions"></el-autocomplete>
        </el-form-item>
        <el-form-item :label="$t('stylegen.secondLineFontSize')">
          <el-input v-model.number="form.secondLineFontSize" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.secondLineLineHeight')">
          <el-input v-model.number="form.secondLineLineHeight" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.secondLineColor')">
          <el-color-picker v-model="form.secondLineColor"></el-color-picker>
        </el-form-item>
        <el-form-item :label="$t('stylegen.scContentLineFont')">
          <el-autocomplete v-model="form.scContentFont" :fetch-suggestions="getFontSuggestions"></el-autocomplete>
        </el-form-item>
        <el-form-item :label="$t('stylegen.scContentLineFontSize')">
          <el-input v-model.number="form.scContentFontSize" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.scContentLineLineHeight')">
          <el-input v-model.number="form.scContentLineHeight" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.scContentLineColor')">
          <el-color-picker v-model="form.scContentColor"></el-color-picker>
        </el-form-item>
        <el-form-item :label="$t('stylegen.showNewMemberBg')">
          <el-switch v-model="form.showNewMemberBg"></el-switch>
        </el-form-item>
        <el-form-item :label="$t('stylegen.showScTicker')">
          <el-switch v-model="form.showScTicker"></el-switch>
        </el-form-item>
        <el-form-item :label="$t('stylegen.showOtherThings')">
          <el-switch v-model="form.showOtherThings"></el-switch>
        </el-form-item>

        <h3>{{$t('stylegen.animation')}}</h3>
        <el-form-item :label="$t('stylegen.animateIn')">
          <el-switch v-model="form.animateIn"></el-switch>
        </el-form-item>
        <el-form-item :label="$t('stylegen.fadeInTime')">
          <el-input v-model.number="form.fadeInTime" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.animateOut')">
          <el-switch v-model="form.animateOut"></el-switch>
        </el-form-item>
        <el-form-item :label="$t('stylegen.animateOutWaitTime')">
          <el-input v-model.number="form.animateOutWaitTime" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.fadeOutTime')">
          <el-input v-model.number="form.fadeOutTime" type="number" min="0"></el-input>
        </el-form-item>
        <el-form-item :label="$t('stylegen.slide')">
          <el-switch v-model="form.slide"></el-switch>
        </el-form-item>
        <el-form-item :label="$t('stylegen.reverseSlide')">
          <el-switch v-model="form.reverseSlide"></el-switch>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="playAnimation">{{$t('stylegen.playAnimation')}}</el-button>
        </el-form-item>

        <h3>{{$t('stylegen.result')}}</h3>
        <el-form-item label="CSS">
          <el-input v-model="result" ref="result" type="textarea" :rows="20"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="copyResult">{{$t('stylegen.copy')}}</el-button>
          <el-button @click="resetConfig">{{$t('stylegen.resetConfig')}}</el-button>
        </el-form-item>
      </el-form>
    </el-col>
    <el-col :span="12">
      <div ref="exampleContainer" id="example-container">
        <div id="fakebody">
          <chat-renderer ref="renderer" :css="exampleCss"></chat-renderer>
        </div>
      </div>
    </el-col>
  </el-row>
</template>

<script>
import _ from 'lodash'

import * as stylegen from './stylegen'
import * as fonts from './fonts'
import ChatRenderer from '@/components/ChatRenderer'
import * as constants from '@/components/ChatRenderer/constants'

let time = new Date()
let textMessageTemplate = {
  id: 0,
  addTime: time,
  type: constants.MESSAGE_TYPE_TEXT,
  avatarUrl: 'https://static.hdslb.com/images/member/noface.gif',
  time: time,
  authorName: '',
  authorType: constants.AUTHRO_TYPE_NORMAL,
  content: '',
  privilegeType: 0,
  repeated: 1,
  translation: ''
}
let membershipItemTemplate = {
  id: 0,
  addTime: time,
  type: constants.MESSAGE_TYPE_MEMBER,
  avatarUrl: 'https://static.hdslb.com/images/member/noface.gif',
  time: time,
  authorName: '',
  privilegeType: 3,
  title: '欢迎上舰'
}
let paidMessageTemplate = {
  id: 0,
  addTime: time,
  type: constants.MESSAGE_TYPE_SUPER_CHAT,
  avatarUrl: 'https://static.hdslb.com/images/member/noface.gif',
  authorName: '',
  price: 0,
  time: time,
  content: '',
  translation: ''
}
let nextId = 0
const EXAMPLE_MESSAGES = [
  {
    ...textMessageTemplate,
    id: (nextId++).toString(),
    authorName: 'mob路人',
    content: '8888888888',
    repeated: 12
  },
  {
    ...textMessageTemplate,
    id: (nextId++).toString(),
    authorName: 'member舰长',
    authorType:  constants.AUTHRO_TYPE_MEMBER,
    content: '草',
    privilegeType: 3,
    repeated: 3
  },
  {
    ...textMessageTemplate,
    id: (nextId++).toString(),
    authorName: 'admin房管',
    authorType: constants.AUTHRO_TYPE_ADMIN,
    content: 'kksk'
  },
  {
    ...membershipItemTemplate,
    id: (nextId++).toString(),
    authorName: '艾米亚official'
  },
  {
    ...paidMessageTemplate,
    id: (nextId++).toString(),
    authorName: '愛里紗メイプル',
    price: 66600,
    content: '投喂 小电视飞船x100'
  },
  {
    ...textMessageTemplate,
    id: (nextId++).toString(),
    authorName: 'streamer主播',
    authorType: constants.AUTHRO_TYPE_OWNER,
    content: '老板大气，老板身体健康'
  },
  {
    ...paidMessageTemplate,
    id: (nextId++).toString(),
    authorName: 'AstralisUP',
    price: 30,
    content: '言いたいことがあるんだよ！'
  }
]

export default {
  name: 'StyleGenerator',
  components: {
    ChatRenderer
  },
  data() {
    let stylegenConfig = stylegen.getLocalConfig()
    let result = stylegen.getStyle(stylegenConfig)
    return {
      FONTS: [...fonts.LOCAL_FONTS, ...fonts.NETWORK_FONTS],

      form: {...stylegenConfig},
      result,
      exampleCss: result.replace(/^body\b/gm, '#fakebody'),
    }
  },
  computed: {
    computedResult() {
      return stylegen.getStyle(this.form)
    }
  },
  watch: {
    computedResult: _.debounce(function(val) {
      this.result = val
      stylegen.setLocalConfig(this.form)
    }, 500),
    result(val) {
      this.exampleCss = val.replace(/^body\b/gm, '#fakebody')
    }
  },
  mounted() {
    this.$refs.renderer.addMessages(EXAMPLE_MESSAGES)

    let observer = new MutationObserver(() => this.$refs.renderer.scrollToBottom())
    observer.observe(this.$refs.exampleContainer, {attributes: true})
  },
  methods: {
    getFontSuggestions(query, callback) {
      let res = this.FONTS.map(font => {return {value: font}})
      if (query) {
        query = query.toLowerCase()
        res = res.filter(
          font => font.value.toLowerCase().indexOf(query) !== -1
        )
      }
      callback(res)
    },
    playAnimation() {
      this.$refs.renderer.clearMessages()
      this.$nextTick(() => this.$refs.renderer.addMessages(EXAMPLE_MESSAGES))
    },
    copyResult() {
      this.$refs.result.select()
      document.execCommand('Copy')
    },
    resetConfig() {
      this.form = {...stylegen.DEFAULT_CONFIG}
    }
  }
}
</script>

<style scoped>
.el-form {
  max-width: 800px;
}

#example-container {
  position: fixed;
  top: 30px;
  left: calc(210px + 40px + (100vw - 210px - 40px) / 2);
  width: calc((100vw - 210px - 40px) / 2 - 40px - 30px);
  height: calc(100vh - 110px);

  background-color: #444;
  background-image:
    -moz-linear-gradient(45deg, #333 25%, transparent 25%),
    -moz-linear-gradient(-45deg, #333 25%, transparent 25%),
    -moz-linear-gradient(45deg, transparent 75%, #333 75%),
    -moz-linear-gradient(-45deg, transparent 75%, #333 75%);
  background-image:
    -webkit-gradient(linear, 0 100%, 100% 0, color-stop(.25, #333), color-stop(.25, transparent)),
    -webkit-gradient(linear, 0 0, 100% 100%, color-stop(.25, #333), color-stop(.25, transparent)),
    -webkit-gradient(linear, 0 100%, 100% 0, color-stop(.75, transparent), color-stop(.75, #333)),
    -webkit-gradient(linear, 0 0, 100% 100%, color-stop(.75, transparent), color-stop(.75, #333));

  -moz-background-size:32px 32px;
  background-size:32px 32px;
  -webkit-background-size:32px 32px;

  background-position:0 0, 16px 0, 16px -16px, 0px 16px;

  padding: 25px;

  resize: both;
  overflow: hidden;
}

.app-wrapper.mobile #example-container {
  display: none;
}

#fakebody {
  outline: 1px #999 dashed;
  height: 100%;
}
</style>
