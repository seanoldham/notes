# Params

Let's say we have two models, `Collection` and `Product`. A `Collection` can have many `Products` and a `Product` can be in many `Collections`. Let's also say that when creating a new `Product`, we already know which `Collections` we want it to be in. We'll want to whitelist the `collection_ids` param in the `products_controller` so we can pass that info when we create our `Product`. Since there could be multiple `Collections` passed, we'll want to write it like this: `params.require(:product).permit(:all, :the, :other, :params, collection_ids: [])`. This allows an array of `Collections` to be passed instead of a single value.