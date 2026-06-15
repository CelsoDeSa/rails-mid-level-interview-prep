Score: 0
Probability: high
Type: coding

# Request Spec for API Endpoint

## Question

How would you test a Rails API endpoint that creates an order?

## Brief Answer

Use a request spec that posts valid/invalid params, checks status codes, response body, database changes, and authorization.

## Comprehensive Explanation

Example RSpec shape:

```ruby
RSpec.describe "Orders", type: :request do
  describe "POST /orders" do
    it "creates an order" do
      user = create(:user)

      expect {
        post orders_path,
          params: { order: { product_id: product.id, quantity: 2 } },
          headers: auth_headers(user)
      }.to change(Order, :count).by(1)

      expect(response).to have_http_status(:created)
    end
  end
end
```

Also test invalid params (`422`), unauthenticated access (`401`), unauthorized access (`403`), and important side effects like enqueued jobs.

## Practice Prompt

Write a request spec for invalid order quantity.
