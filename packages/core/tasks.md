1. Create a core with database operation

like

```ts
await sdk.products.list({
  where: {
    title: "test",
  },
});
```

2. Create a section in config where you can extend core models like product variant etc in a type safe manner

```ts
{
  customFields: {
    product: [{
      name: 'type',
      type: 'string'
      nullable: true
    }]
  }
}
``;
```

Also make sure you can create some relations between these custom attributes

```ts
{
  customAttributes: {
    product: {
      customField: "string";
      relation: () => myCustomModel.id;
      relationType: "oneToOne";
    }
  }
}
``;
```

Make sure these changes would reflected in database operations. Like:

```ts
await sdk.products.list({
  fields: ["customField"], // you could see it in typescript
});
```

3. Create a core logic for cart, product etc

4. introduce modules

like

core/
seller/
index.ts

```ts
// index.ts
import { Module } from "myframework";
import * as handlers from "./seller-service";

export const SellerModule = Module({
  handlers,
});
```

```ts
// seller-service.ts

export const createSeller = (input: { name: string }, ctx) => {
  const { db } = ctx;
};
```

then these modules are being added to config

5. Introduce hooks in config

```ts
{
  hooks: {
    order: {
      createData: async (input, ctx) => {
        const { framework } = ctx;

        const seller = await framework.sellers.retrieve({
          id: input.metadata.id,
        });

        return {
          ...input,
          seller_id: seller.id,
        };
      };
    }
  }
}
``;
```

6. introduce events

7. introduce CLI
