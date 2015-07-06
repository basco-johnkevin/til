### Ordering nested eager loaded associations
```
Customer.find({
  where: {
    id: id,
    CompanyId: req.company.id
  },
  include: [
    {
      model: Ticket,
      include: [
        { model: User, as: 'Assignee' },
        { model: Comment },
        { model: Label }
      ],

    }
  ],
  order: [[Ticket, 'createdAt', 'DESC'], [Ticket, Comment, 'createdAt', 'ASC']]
});
```
