<template>
<span :class="classes" :aria-label="accessibilityLabel">
    <div v-if="source == 'placeholder' || !finalSource" class="Polaris-Icon__Placeholder"></div>
    <svg
        v-if="source != 'placeholder' && finalSource"
        class="Polaris-Icon__Svg"
        :viewBox="finalSource.viewBox"
        v-html="finalSource.body"/>
</span>
</template>


<script>
import SvgSource from '../SvgSource.js';

import add from '!!raw-loader!../resources/icons/add.svg';
import alert from '!!raw-loader!../resources/icons/alert.svg';
import arrowDown from '!!raw-loader!../resources/icons/arrow-down.svg';
import arrowLeft from '!!raw-loader!../resources/icons/arrow-left.svg';
import arrowRight from '!!raw-loader!../resources/icons/arrow-right.svg';
import arrowUp from '!!raw-loader!../resources/icons/arrow-up.svg';
import arrowUpDown from '!!raw-loader!../resources/icons/arrow-up-down.svg';
import calendar from '!!raw-loader!../resources/icons/calendar.svg';
import cancel from '!!raw-loader!../resources/icons/cancel.svg';
import cancelSmall from '!!raw-loader!../resources/icons/cancel-small.svg';
import caretDown from '!!raw-loader!../resources/icons/caret-down.svg';
import caretUp from '!!raw-loader!../resources/icons/caret-up.svg';
import checkmark from '!!raw-loader!../resources/icons/checkmark.svg';
import chevronDown from '!!raw-loader!../resources/icons/chevron-down.svg';
import chevronLeft from '!!raw-loader!../resources/icons/chevron-left.svg';
import chevronRight from '!!raw-loader!../resources/icons/chevron-right.svg';
import chevronUp from '!!raw-loader!../resources/icons/chevron-up.svg';
import circleCancel from '!!raw-loader!../resources/icons/circle-cancel.svg';
import circleChevronDown from '!!raw-loader!../resources/icons/circle-chevron-down.svg';
import circleChevronLeft from '!!raw-loader!../resources/icons/circle-chevron-left.svg';
import circleChevronRight from '!!raw-loader!../resources/icons/circle-chevron-right.svg';
import circleChevronUp from '!!raw-loader!../resources/icons/circle-chevron-up.svg';
import circlePlus from '!!raw-loader!../resources/icons/circle-plus.svg';
import conversation from '!!raw-loader!../resources/icons/conversation.svg';
import deleteIcon from '!!raw-loader!../resources/icons/delete.svg';
import disable from '!!raw-loader!../resources/icons/disable.svg';
import dispute from '!!raw-loader!../resources/icons/dispute.svg';
import duplicate from '!!raw-loader!../resources/icons/duplicate.svg';
import embed from '!!raw-loader!../resources/icons/embed.svg';
import enableSelection from '!!raw-loader!../resources/icons/enable-selection.svg';
import exportIcon from '!!raw-loader!../resources/icons/export.svg';
import external from '!!raw-loader!../resources/icons/external.svg';
import help from '!!raw-loader!../resources/icons/help.svg';
import horizontalDots from '!!raw-loader!../resources/icons/horizontal-dots.svg';
import importIcon from '!!raw-loader!../resources/icons/import.svg';
import notes from '!!raw-loader!../resources/icons/notes.svg';
import print from '!!raw-loader!../resources/icons/print.svg';
import refresh from '!!raw-loader!../resources/icons/refresh.svg';
import risk from '!!raw-loader!../resources/icons/risk.svg';
import save from '!!raw-loader!../resources/icons/save.svg';
import search from '!!raw-loader!../resources/icons/search.svg';
import subtract from '!!raw-loader!../resources/icons/subtract.svg';
import view from '!!raw-loader!../resources/icons/view.svg';
import toggleOn from '!!raw-loader!../resources/icons/toggle-on.svg';
import toggleOff from '!!raw-loader!../resources/icons/toggle-off.svg';
import settings from '!!raw-loader!../resources/icons/settings.svg';
import spinnerLarge from '!!raw-loader!../resources/spinner-large.svg';
import spinnerSmall from '!!raw-loader!../resources/spinner-small.svg'

export const BUNDLED_ICONS = {
    add,
    alert,
    arrowDown,
    arrowLeft,
    arrowRight,
    arrowUp,
    arrowUpDown,
    calendar,
    cancel,
    cancelSmall,
    caretDown,
    caretUp,
    checkmark,
    chevronDown,
    chevronLeft,
    chevronRight,
    chevronUp,
    circleCancel,
    circleChevronDown,
    circleChevronLeft,
    circleChevronRight,
    circleChevronUp,
    circlePlus,
    conversation,
    delete: deleteIcon,
    disable,
    dispute,
    duplicate,
    embed,
    enableSelection,
    export: exportIcon,
    external,
    help,
    horizontalDots,
    import: importIcon,
    notes,
    print,
    refresh,
    risk,
    save,
    search,
    subtract,
    view,
    toggleOn,
    toggleOff,
    settings,
    spinnerLarge,
    spinnerSmall
};

export default {
    props: {
        source: {
            type: String,
            required: true
        },
        color: {
            type: String
        },
        backdrop: {
            type: Boolean
        },
        accessibilityLabel: String
    },
    computed: {
        finalSource() {
            var svgSource = this.source;
            if (typeof this.source == 'string') {
                const bundled = BUNDLED_ICONS[this.source];
                if (bundled) {
                    svgSource = bundled;
                }
            }
            try {
                var svgObject = SvgSource.parseSVG(svgSource);
                return svgObject;
            } catch (e) {
                return null;
            }
        },
        classes() {
            var r = {
                'Polaris-Icon': true,
                'Polaris-Icon--hasBackdrop': this.backdrop
            };
            if (this.color) {
                var valueTag = this.color.charAt(0).toUpperCase()+this.color.slice(1);
                r['Polaris-Icon--color'+valueTag] = true;
            }
            return r;
        }
    }
};
</script>
