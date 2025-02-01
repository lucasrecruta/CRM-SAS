import React from 'react';
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs";
import { Table, TableBody, TableCell, TableHead, TableHeader, TableRow } from "@/components/ui/table";
import { PlusCircle, User, Users } from "lucide-react";

export default function CRMApp() {
  return (
    <div className="min-h-screen bg-gray-100 text-gray-800">
      <header className="bg-purple-700 text-white p-4">
        <h1 className="text-2xl font-bold">CRM SaaS</h1>
      </header>

      <main className="p-4">
        <Tabs defaultValue="individual" className="container mx-auto">
          <TabsList>
            <TabsTrigger value="individual"><User className="mr-2" /> Individuals</TabsTrigger>
            <TabsTrigger value="companies"><Users className="mr-2" /> Companies</TabsTrigger>
          </TabsList>

          <TabsContent value="individual">
            <Section title="Manage Individuals">
              <AddEntryForm type="Individual" />
              <DataTable type="Individuals" />
            </Section>
          </TabsContent>

          <TabsContent value="companies">
            <Section title="Manage Companies">
              <AddEntryForm type="Company" />
              <DataTable type="Companies" />
            </Section>
          </TabsContent>
        </Tabs>
      </main>
    </div>
  );
}

function Section({ title, children }) {
  return (
    <Card className="mt-4">
      <CardContent>
        <h2 className="text-xl font-semibold mb-4">{title}</h2>
        {children}
      </CardContent>
    </Card>
  );
}

function AddEntryForm({ type }) {
  return (
    <form className="mb-4 flex gap-2">
      <Input placeholder={`${type} Name`} className="flex-1" />
      <Input placeholder="Email" className="flex-1" />
      <Button><PlusCircle className="mr-2" /> Add {type}</Button>
    </form>
  );
}

function DataTable({ type }) {
  return (
    <Table>
      <TableHeader>
        <TableRow>
          <TableHead>Name</TableHead>
          <TableHead>Email</TableHead>
          <TableHead>Actions</TableHead>
        </TableRow>
      </TableHeader>
      <TableBody>
        {/* Example Data */}
        <TableRow>
          <TableCell>John Doe</TableCell>
          <TableCell>john.doe@example.com</TableCell>
          <TableCell>
            <Button variant="secondary" size="sm">Edit</Button>
            <Button variant="destructive" size="sm" className="ml-2">Delete</Button>
          </TableCell>
        </TableRow>
      </TableBody>
    </Table>
  );
}
