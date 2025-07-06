import React, { useState } from "react"; import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";

const translations = { ar: { siteName: "شركة الديكور الفاخر", home: "الرئيسية", about: "من نحن", services: "خدماتنا", contact: "تواصل معنا", welcome: "مرحبًا بكم في شركة الديكور الفاخر", description: "نُحول المساحات العادية إلى أماكن تنبض بالجمال والأناقة", aboutText: "نحن شركة متخصصة في التصميم الداخلي والديكور، نمتلك خبرة طويلة في تحويل الأفكار إلى واقع ملموس يعكس ذوق العميل ويلبي احتياجاته بأعلى جودة.", servicesList: [ "تصميم داخلي سكني وتجاري", "تنسيق ألوان ومساحات", "تركيب ديكورات جبسية وإضاءة مخفية", "تنفيذ أثاث حسب الطلب" ], contactText: "للتواصل أو طلب استشارة، يرجى مراسلتنا على البريد الإلكتروني:", }, en: { siteName: "Luxury Decor Company", home: "Home", about: "About Us", services: "Our Services", contact: "Contact Us", welcome: "Welcome to Luxury Decor Company", description: "We transform ordinary spaces into beautiful and elegant places.", aboutText: "We are a specialized interior design company with extensive experience in turning ideas into a reality that reflects the client's taste and meets their needs with high quality.", servicesList: [ "Residential and commercial interior design", "Color and space coordination", "Gypsum decorations and hidden lighting", "Custom furniture execution" ], contactText: "For inquiries or consultation, please email us at:" } };

const Navbar = ({ lang, switchLang }) => { const t = translations[lang]; return ( <nav className="bg-gradient-to-r from-amber-800 to-yellow-600 text-white p-4 shadow-xl flex justify-between items-center"> <h1 className="text-2xl font-bold">{t.siteName}</h1> <ul className="flex gap-6 text-lg"> <li><Link to="/">{t.home}</Link></li> <li><Link to="/about">{t.about}</Link></li> <li><Link to="/services">{t.services}</Link></li> <li><Link to="/contact">{t.contact}</Link></li> <li> <button onClick={switchLang} className="underline">{lang === 'ar' ? 'English' : 'عربي'}</button> </li> </ul> </nav> ); };

const Home = ({ lang }) => { const t = translations[lang]; return ( <section className="p-8 text-center bg-yellow-50 min-h-screen"> <h2 className="text-4xl font-bold text-amber-800 mb-4">{t.welcome}</h2> <p className="text-lg text-gray-700">{t.description}</p> </section> ); };

const About = ({ lang }) => { const t = translations[lang]; return ( <section className="p-8 bg-white min-h-screen"> <h2 className="text-3xl text-amber-700 font-semibold mb-4">{t.about}</h2> <p className="text-gray-700 leading-relaxed">{t.aboutText}</p> </section> ); };

const Services = ({ lang }) => { const t = translations[lang]; return ( <section className="p-8 bg-yellow-100 min-h-screen"> <h2 className="text-3xl text-amber-700 font-semibold mb-4">{t.services}</h2> <ul className="list-disc pl-6 text-gray-700"> {t.servicesList.map((item, index) => <li key={index}>{item}</li>)} </ul> </section> ); };

const Contact = ({ lang }) => { const t = translations[lang]; return ( <section className="p-8 bg-white min-h-screen"> <h2 className="text-3xl text-amber-700 font-semibold mb-4">{t.contact}</h2> <p className="text-gray-700">{t.contactText} <a href="mailto:info@decorluxury.com" className="text-amber-800 underline">info@decorluxury.com</a></p> </section> ); };

const App = () => { const [lang, setLang] = useState("ar"); const switchLang = () => setLang(lang === "ar" ? "en" : "ar");

return ( <Router> <Navbar lang={lang} switchLang={switchLang} /> <Routes> <Route path="/" element={<Home lang={lang} />} /> <Route path="/about" element={<About lang={lang} />} /> <Route path="/services" element={<Services lang={lang} />} /> <Route path="/contact" element={<Contact lang={lang} />} /> </Routes> </Router> ); };

export default App;

# My-deco-site