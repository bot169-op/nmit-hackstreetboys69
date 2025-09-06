# nmit-hackstreetboys69
odoo X nmit hackacthon
const express = require('express');
const cors = require('cors');
const app = express();

app.use(cors());
app.use(express.json());

const listings = [
  { id: 1, title: 'Eco-friendly Backpack', description: 'Upcycled materials, gently used.', price: 1200 },
  { id: 2, title: 'Organic Cotton Dress', description: 'Certified organic, zero waste.', price: 900 }
];

app.get('/api/listings', (req, res) => {
  res.json(listings);
});

const PORT = 5000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));

import React, { useState, useEffect } from 'react';
import { View, Text, FlatList, Button, StyleSheet } from 'react-native';

export default function App() {
  const [listings, setListings] = useState([]);

  useEffect(() => {
    fetch('http://localhost:5000/api/listings')
      .then(res => res.json())
      .then(data => setListings(data))
      .catch(err => console.error(err));
  }, []);

  return (
    <View style={styles.container}>
      <Text style={styles.title}>EcoFinds</Text>
      <FlatList
        data={listings}
        keyExtractor={(item) => item.id.toString()}
        renderItem={({ item }) => (
          <View style={styles.card}>
            <Text style={styles.itemTitle}>{item.title}</Text>
            <Text>{item.description}</Text>
            <Text style={styles.price}>₹{item.price}</Text>
            <Button title="Buy Now" onPress={() => alert('Buy feature coming soon!')} />
          </View>
        )}
      />
    </View>
  );
}
node_modules/

const styles = StyleSheet.create({
  container: { flex: 1, marginTop: 50, padding: 20, backgroundColor: '#f5fff5' },
  title: { fontSize: 24, fontWeight: 'bold', marginBottom: 20, color: '#2d6b2d' },
  card: { marginBottom: 15, padding: 15, backgroundColor: 'white', borderRadius: 8, elevation: 3 },
  itemTitle: { fontSize: 18, fontWeight: '600' },
  price: { marginTop: 5, marginBottom: 10, color: '#2d6b2d', fontWeight: 'bold' },
});
node_modules/
.expo/

