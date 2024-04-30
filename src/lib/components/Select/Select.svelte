<script lang="ts">
  import type { AsChildType } from "$lib/index.js"
  import { cn } from "$lib/index.js"
  import { type CreateSelectProps } from "@melt-ui/svelte"
  import { tv } from "tailwind-variants"
  import ctx from "./ctx.js"

  type $$Props = Omit<CreateSelectProps<boolean>, "arrowSize"> & AsChildType

  export let asChild: $$Props["asChild"] = false
  export let forceVisible: $$Props["forceVisible"] = true
  export { className as class }

  let className = ""

  const style = tv({
    base: cn`
      flex
      flex-col
      gap-2
    `,
  })

  ctx.set({ ...$$restProps, forceVisible })
</script>

{#if asChild}
  <slot />
{:else}
  <div class={cn(style.base, className)} {...$$restProps}>
    <slot />
  </div>
{/if}
