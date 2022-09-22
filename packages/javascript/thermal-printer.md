Example:

```js
import createPrinter from '@ombori/ga-thermal-printer';

export default function printTicket(ticket: string) {
  if (printer) {
    printer.alignCenter();
    printer.setTextQuadArea();
    printer.bold(true);
    printer.newLine();
    printer.setTextSize(4, 4);
    printer.println(ticket);
    printer.partialCut();
    return printer.execute();
  } else {
    throw new Error('Error printing ticket');
  }
}
```