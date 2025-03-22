<script>
  import { onMount } from 'svelte';
  import { cart, addToCart, removeFromCart } from '$lib/stores/cart';
  import { ShoppingCart, X, Plus, Minus, ArrowRight } from 'lucide-svelte';
  import { Button } from '$lib/components/ui/button';
  import { Badge } from '$lib/components/ui/badge';
  import { Separator } from '$lib/components/ui/separator';
  import { DropdownMenu, DropdownMenuContent, DropdownMenuTrigger } from '$lib/components/ui/DropdownMenu.svelte';
  import { get } from 'svelte/store';

  let open = true;
  let items = [];

  onMount(() => {
    cart.subscribe(value => {
      items = value;
    });
  });

  const totalItems = () => items.reduce((sum, item) => sum + item.quantity, 0);
  const subtotal = () => items.reduce((sum, item) => sum + item.price * item.quantity, 0);

  function onCheckout() {
    console.log("Checkout clicked");
  }

  function onRemoveItem(id) {
    removeFromCart(id);
  }

  function onUpdateQuantity(id, quantity) {
    if (quantity > 0) {
      const item = items.find(item => item.id === id);
      if (item) {
        item.quantity = quantity;
        cart.set([...items]);
      }
    }
  }
</script>

<div class="relative bg-white">
  <DropdownMenu bind:open>
    <DropdownMenuTrigger asChild>
      <Button variant="ghost" size="icon" class="relative">
        <ShoppingCart class="h-5 w-5" />
        {#if totalItems() > 0}
          <Badge variant="destructive" class="absolute -top-2 -right-2 h-5 w-5 flex items-center justify-center p-0 text-xs">
            {totalItems()}
          </Badge>
        {/if}
      </Button>
    </DropdownMenuTrigger>
    <DropdownMenuContent align="end" class="w-80 p-4 bg-white" sideOffset={8}>
      <div class="flex justify-between items-center mb-4">
        <h3 class="font-bold text-lg">Your Cart</h3>
        <Button variant="ghost" size="sm" on:click={() => open = false}>
          <X class="h-4 w-4" />
        </Button>
      </div>

      {#if items.length === 0}
        <div class="py-6 text-center">
          <p class="text-gray-500">Your cart is empty</p>
          <Button variant="outline" class="mt-4" on:click={() => open = false}>
            Continue Shopping
          </Button>
        </div>
      {:else}
        <div class="max-h-[300px] overflow-y-auto space-y-4 pr-1">
          {#each items as item (item.id)}
            <div class="flex gap-3">
              <div class="h-16 w-16 rounded-md overflow-hidden flex-shrink-0">
                <img src={item.image} alt={item.name} class="h-full w-full object-cover" />
              </div>
              <div class="flex-1">
                <h4 class="text-sm font-medium line-clamp-1">{item.name}</h4>
                <div class="flex items-center mt-1 space-x-2">
                  <div class="flex items-center border rounded-md">
                    <Button variant="ghost" size="icon" class="h-7 w-7 p-0" on:click={() => onUpdateQuantity(item.id, Math.max(1, item.quantity - 1))} disabled={item.quantity <= 1}>
                      <Minus class="h-3 w-3" />
                    </Button>
                    <span class="w-8 text-center text-sm">{item.quantity}</span>
                    <Button variant="ghost" size="icon" class="h-7 w-7 p-0" on:click={() => onUpdateQuantity(item.id, item.quantity + 1)}>
                      <Plus class="h-3 w-3" />
                    </Button>
                  </div>
                  <Button variant="ghost" size="sm" class="h-7 px-2 text-xs text-red-500 hover:text-red-700 hover:bg-red-50" on:click={() => onRemoveItem(item.id)}>
                    Remove
                  </Button>
                </div>
              </div>
              <div class="text-right">
                <p class="font-medium">${item.price.toFixed(2)}</p>
              </div>
            </div>
          {/each}
        </div>

        <Separator class="my-4" />

        <div class="space-y-3">
          <div class="flex justify-between">
            <span class="text-sm text-gray-500">Subtotal</span>
            <span class="font-medium">${subtotal().toFixed(2)}</span>
          </div>
          <div class="flex justify-between">
            <span class="text-sm text-gray-500">Shipping</span>
            <span class="text-sm">Calculated at checkout</span>
          </div>
          <Separator class="my-2" />
          <div class="flex justify-between font-bold">
            <span>Total</span>
            <span>${subtotal().toFixed(2)}</span>
          </div>
          <Button class="w-full mt-4 gap-2" on:click={onCheckout}>
            Checkout <ArrowRight class="h-4 w-4" />
          </Button>
          <Button variant="outline" class="w-full mt-2" on:click={() => open = false}>
            Continue Shopping
          </Button>
        </div>
      {/if}
    </DropdownMenuContent>
  </DropdownMenu>
</div>
