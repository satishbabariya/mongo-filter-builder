# mongo-filter-builder 

## Quick examples

```golang

package main

import (
	"context"

	"github.com/satishbabariya/mongo-filter-builder"
	"go.mongodb.org/mongo-driver/mongo"
	"go.mongodb.org/mongo-driver/mongo/options"
)

func main() {
	ctx := context.TODO()
	client, _ := mongo.Connect(ctx, options.Client().ApplyURI("mongodb://localhost:27017"))
	collection := client.Database("testing").Collection("test")
	doc := greenleaf.M{"name": "Jhon", "tags": []string{"fast", "furious"}, "score": 128, "coins": 10000, "active": true}
	collection.InsertOne(ctx, doc)

	// filter selector.
	filter := greenleaf.
		Filter().
		EqString("name", "Jhon").
		InString("tags", []string{"fast", "furious"}).
		GtInt("score", 100).
		LteInt("score", 200).
		Exists("active", true).
		Build()
}

```
