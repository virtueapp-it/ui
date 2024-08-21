<script lang="ts">
  import { type CreateContextMenuProps } from "@melt-ui/svelte"
  import ctx from "./ctx.js"

  type $$Props = Omit<CreateContextMenuProps, "arrowSize">

  export let forceVisible: $$Props["forceVisible"] = true

  ctx.set({ ...$$restProps, forceVisible })
</script>

<slot />
