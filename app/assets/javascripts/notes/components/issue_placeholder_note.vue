<script>
  import { mapGetters } from 'vuex';
  import userAvatarLink from '../../vue_shared/components/user_avatar/user_avatar_link.vue';

  export default {
    name: 'issuePlaceholderNote',
    props: {
      note: {
        type: Object,
        required: true,
      },
    },
    components: {
      userAvatarLink,
    },
    computed: {
      ...mapGetters([
        'getUserData',
      ]),
    },
  };
</script>

<template>
  <li class="note being-posted fade-in-half timeline-entry">
    <div class="timeline-entry-inner">
      <div class="timeline-icon">
        <user-avatar-link
          :link-href="getUserData.path"
          :img-src="getUserData.avatar_url"
          :img-size="40"
          />
      </div>
      <div
        :class="{ discussion: !note.individual_note }"
        class="timeline-content">
        <div class="note-header">
          <div class="note-header-info">
            <a :href="getUserData.path">
              <span class="hidden-xs">{{getUserData.name}}</span>
              <span class="note-headline-light">@{{getUserData.username}}</span>
            </a>
          </div>
        </div>
        <div class="note-body">
          <div class="note-text">
            <p>{{note.body}}</p>
          </div>
        </div>
      </div>
    </div>
  </li>
</template>
