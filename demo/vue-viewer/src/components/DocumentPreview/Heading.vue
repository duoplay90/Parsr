<template functional>
  <g>
    <rect
      class="Heading"
      :id="'Heading_' + props.element.id"
      :key="props.element.id"
      :x="props.element.box.l"
      :y="props.element.box.t"
      :width="props.element.box.w"
      :height="props.element.box.h"
    />
    <component
      :is="props.components.LineElement"
      v-for="element in props.element.content"
      :key="element.id"
      :element="element"
      :fonts="props.fonts"
      @custom-event="listeners['custom-event']"
    ></component>
  </g>
</template>

<script>
import LineElement from '@/components/DocumentPreview/Line';
import pageElementMixin from '@/mixins/pageElementMixin';

export default {
  props: {
    components: {
      type: Object,
      default() {
        return {
          LineElement,
        };
      },
    },
  },
  mixins: [pageElementMixin],
};
</script>
