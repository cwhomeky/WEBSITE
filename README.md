import React, { useState } from 'react';
import { 
  Wand2, 
  Upload, 
  Sparkles, 
  Image as ImageIcon, 
  Video, 
  Share2, 
  CheckCircle, 
  Edit3 
} from 'lucide-react';

// ----------------------------------------------------
// 1. STANDARD RESO WEB API / MLS FIELD MAPPER
// ----------------------------------------------------
const mapMlsToAdSchema = (rawMlsData) => {
  return {
    listingKey: rawMlsData.ListingKey || rawMlsData.MLS_ID || '',
    address: rawMlsData.UnparsedAddress || rawMlsData.Address || rawMlsData.FullAddress || '',
    city: rawMlsData.City || '',
    state: rawMlsData.StateOrProvince || rawMlsData.State || '',
    zip: rawMlsData.PostalCode || rawMlsData.Zip || '',
    price: rawMlsData.ListPrice ? `$${Number(rawMlsData.ListPrice).toLocaleString()}` : '',
    beds: rawMlsData.BedroomsTotal || rawMlsData.Beds || '',
    baths: rawMlsData.BathroomsTotalInteger || rawMlsData.Baths || '',
    sqft: rawMlsData.BuildingAreaTotal || rawMlsData.SqFt || '',
    yearBuilt: rawMlsData.YearBuilt || '',
    propertyType: rawMlsData.PropertySubType || rawMlsData.PropertyType || 'Single Family',
    publicRemarks: rawMlsData.PublicRemarks || rawMlsData.Description || '',
    media: rawMlsData.Media || rawMlsData.Photos || [],
    
    // AI & Custom Marketing Fields (Populated/Generated)
    headline: '',
    socialCaption: '',
    shortFormHook: '',
    hashtags: '',
    aiTargetAudience: 'First-time buyers, move-up families, or local buyers',
  };
};

// ----------------------------------------------------
// 2. MAIN AD EDITOR & AUTO-POPULATOR COMPONENT
// ----------------------------------------------------
export default function MlsAdStudio() {
  const [adData, setAdData] = useState({
    listingKey: '',
    address: '',
    city: '',
    state: '',
    zip: '',
    price: '',
    beds: '',
    baths: '',
    sqft: '',
    yearBuilt: '',
    propertyType: '',
    publicRemarks: '',
    headline: '',
    socialCaption: '',
    shortFormHook: '',
    hashtags: '',
    media: [],
  });

  const [isAiLoading, setIsAiLoading] = useState(false);
  const [statusMsg, setStatusMsg] = useState('');

  // Universal Field Change Handler (Allows full manual control over everything)
  const handleChange = (field, value) => {
    setAdData((prev) => ({ ...prev, [field]: value }));
  };

  // --------------------------------------------------
  // MLS UPLOAD & AUTO-POPULATION HANDLER
  // --------------------------------------------------
  const handleMlsUpload = (e) => {
    const file = e.target.files[0];
    if (!file) return;

    setStatusMsg('Parsing MLS Payload...');

    const reader = new FileReader();
    reader.onload = (event) => {
      try {
        let rawData;
        if (file.name.endsWith('.json')) {
          rawData = JSON.parse(event.target.result);
        } else {
          // Mock CSV or alternative structure fallback parsing
          alert('Uploaded MLS payload successfully read.');
          return;
        }

        // Map MLS standardized schema to form state
        const mapped = mapMlsToAdSchema(rawData);
        setAdData(mapped);
        setStatusMsg('Successfully auto-populated from MLS!');
      } catch (err) {
        console.error('Failed to parse file:', err);
        setStatusMsg('Error parsing MLS file. Please check format.');
      }
    };

    reader.readAsText(file);
  };

  // Demo Fetch from RESO Web API
  const simulateResoApiFetch = () => {
    setStatusMsg('Fetching from RESO Web API Endpoint...');
    setTimeout(() => {
      const mockApiData = {
        ListingKey: 'MLS-2026-88910',
        UnparsedAddress: '1248 Oakridge Drive',
        City: 'Elizabethtown',
        StateOrProvince: 'KY',
        PostalCode: '42701',
        ListPrice: 385000,
        BedroomsTotal: 4,
        BathroomsTotalInteger: 3,
        BuildingAreaTotal: 2650,
        YearBuilt: 2021,
        PropertySubType: 'Single Family Residence',
        PublicRemarks: 'Stunning 4-bedroom home featuring an open layout, upgraded granite kitchen countertops, covered back porch, and split-bedroom design.',
        Media: ['https://images.unsplash.com/photo-1568605117036-5fe5e7bab0b7?auto=format&fit=crop&w=800&q=80']
      };
      
      setAdData(mapMlsToAdSchema(mockApiData));
      setStatusMsg('Auto-populated directly from MLS Web API!');
    }, 800);
  };

  // --------------------------------------------------
  // 2026 A.I. EFFECT & MARKETING GENERATORS
  // --------------------------------------------------

  // 1. AI Copywriting & Social Pack
  const generateAiCopy = async () => {
    setIsAiLoading(true);
    setStatusMsg('AI generating optimized listing copy & social suite...');

    // Simulating call to LLM API
    setTimeout(() => {
      const priceText = adData.price || '$385,000';
      const cityText = adData.city || 'local market';

      setAdData((prev) => ({
        ...prev,
        headline: `🔥 JUST LISTED in ${cityText}: Modern ${prev.beds}BD/${prev.baths}BA Beauty!`,
        socialCaption: `Looking for space, style, and move-in ready comfort? Welcome to ${prev.address || 'your next home'}! Featuring ${prev.sqft || '2,500+'} sq ft, an upgraded layout, and premium finishes throughout. Priced at ${priceText}.\n\n📩 DM us today for a private tour or full floor plan details!`,
        shortFormHook: `"Stop scrolling if you've been looking for a 4-bedroom home in ${cityText} under ${priceText}!"`,
        hashtags: `#JustListed #${cityText.replace(/\s+/g, '')}RealEstate #HomeForSale #HouseHunting #PenningtonProperties #PropertyTour`,
      }));

      setIsAiLoading(false);
      setStatusMsg('AI Copy & Marketing Suite Generated!');
    }, 1200);
  };

  // 2. AI Visual Enhancer & Staging Trigger
  const triggerAiVisualEnhancements = () => {
    if (!adData.media.length) {
      alert('Please populate MLS photos first!');
      return;
    }
    setStatusMsg('Applying AI Twilight & Virtual Sky Enhancement...');
    setTimeout(() => {
      setStatusMsg('AI Visual Enhancements applied to listing photo set!');
    }, 1000);
  };

  return (
    <div className="max-w-6xl mx-auto p-6 bg-slate-900 text-slate-100 rounded-xl shadow-2xl border border-slate-800">
      
      {/* HEADER & API / MLS INPUT CONTROLS */}
      <div className="flex flex-col md:flex-row justify-between items-start md:items-center pb-6 border-b border-slate-800 gap-4">
        <div>
          <h1 className="text-2xl font-bold bg-gradient-to-r from-blue-400 to-indigo-400 bg-clip-text text-transparent flex items-center gap-2">
            <Sparkles className="w-6 h-6 text-blue-400" /> MLS Auto-Population & AI Ad Studio
          </h1>
          <p className="text-slate-400 text-sm mt-1">Import from RESO Web API / MLS → Edit anything → Generate 2026 AI Ads</p>
        </div>

        <div className="flex flex-wrap items-center gap-3">
          <button 
            onClick={simulateResoApiFetch}
            className="flex items-center gap-2 px-4 py-2 bg-slate-800 hover:bg-slate-700 text-blue-400 font-medium rounded-lg border border-blue-500/30 transition text-sm"
          >
            <Upload className="w-4 h-4" /> Import from RESO API
          </button>

          <label className="flex items-center gap-2 px-4 py-2 bg-indigo-600 hover:bg-indigo-500 text-white font-medium rounded-lg cursor-pointer transition text-sm">
            <Upload className="w-4 h-4" /> Upload MLS JSON
            <input type="file" accept=".json,.csv" onChange={handleMlsUpload} className="hidden" />
          </label>
        </div>
      </div>

      {statusMsg && (
        <div className="my-4 p-3 bg-blue-950/60 border border-blue-500/40 rounded-lg text-blue-300 text-sm flex items-center gap-2">
          <CheckCircle className="w-4 h-4 text-blue-400" /> {statusMsg}
        </div>
      )}

      {/* MAIN TWO-COLUMN CONTENT AREA */}
      <div className="grid grid-cols-1 lg:grid-cols-12 gap-8 mt-6">
        
        {/* LEFT COLUMN: AUTO-POPULATED / MANUALLY EDITABLE DATA FIELDS */}
        <div className="lg:col-span-7 space-y-5">
          <h2 className="text-lg font-semibold text-slate-200 flex items-center gap-2">
            <Edit3 className="w-5 h-5 text-indigo-400" /> Listing Data (Auto-Populated & Fully Editable)
          </h2>

          <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
            <div>
              <label className="block text-xs font-medium text-slate-400 mb-1">MLS Listing ID</label>
              <input 
                type="text" 
                value={adData.listingKey} 
                onChange={(e) => handleChange('listingKey', e.target.value)}
                className="w-full bg-slate-800 border border-slate-700 rounded-lg p-2.5 text-sm focus:border-indigo-500 focus:outline-none"
              />
            </div>
            <div>
              <label className="block text-xs font-medium text-slate-400 mb-1">List Price</label>
              <input 
                type="text" 
                value={adData.price} 
                onChange={(e) => handleChange('price', e.target.value)}
                className="w-full bg-slate-800 border border-slate-700 rounded-lg p-2.5 text-sm text-green-400 font-semibold focus:border-indigo-500 focus:outline-none"
              />
            </div>
          </div>

          <div>
            <label className="block text-xs font-medium text-slate-400 mb-1">Street Address</label>
            <input 
              type="text" 
              value={adData.address} 
              onChange={(e) => handleChange('address', e.target.value)}
              className="w-full bg-slate-800 border border-slate-700 rounded-lg p-2.5 text-sm focus:border-indigo-500 focus:outline-none"
            />
          </div>

          <div className="grid grid-cols-3 gap-3">
            <div>
              <label className="block text-xs font-medium text-slate-400 mb-1">City</label>
              <input 
                type="text" 
                value={adData.city} 
                onChange={(e) => handleChange('city', e.target.value)}
                className="w-full bg-slate-800 border border-slate-700 rounded-lg p-2.5 text-sm focus:border-indigo-500 focus:outline-none"
              />
            </div>
            <div>
              <label className="block text-xs font-medium text-slate-400 mb-1">State</label>
              <input 
                type="text" 
                value={adData.state} 
                onChange={(e) => handleChange('state', e.target.value)}
                className="w-full bg-slate-800 border border-slate-700 rounded-lg p-2.5 text-sm focus:border-indigo-500 focus:outline-none"
              />
            </div>
            <div>
              <label className="block text-xs font-medium text-slate-400 mb-1">Zip Code</label>
              <input 
                type="text" 
                value={adData.zip} 
                onChange={(e) => handleChange('zip', e.target.value)}
                className="w-full bg-slate-800 border border-slate-700 rounded-lg p-2.5 text-sm focus:border-indigo-500 focus:outline-none"
              />
            </div>
          </div>

          <div className="grid grid-cols-4 gap-3">
            <div>
              <label className="block text-xs font-medium text-slate-400 mb-1">Beds</label>
              <input 
                type="text" 
                value={adData.beds} 
                onChange={(e) => handleChange('beds', e.target.value)}
                className="w-full bg-slate-800 border border-slate-700 rounded-lg p-2 text-sm text-center"
              />
            </div>
            <div>
              <label className="block text-xs font-medium text-slate-400 mb-1">Baths</label>
              <input 
                type="text" 
                value={adData.baths} 
                onChange={(e) => handleChange('baths', e.target.value)}
                className="w-full bg-slate-800 border border-slate-700 rounded-lg p-2 text-sm text-center"
              />
            </div>
            <div>
              <label className="block text-xs font-medium text-slate-400 mb-1">SqFt</label>
              <input 
                type="text" 
                value={adData.sqft} 
                onChange={(e) => handleChange('sqft', e.target.value)}
                className="w-full bg-slate-800 border border-slate-700 rounded-lg p-2 text-sm text-center"
              />
            </div>
            <div>
              <label className="block text-xs font-medium text-slate-400 mb-1">Built</label>
              <input 
                type="text" 
                value={adData.yearBuilt} 
                onChange={(e) => handleChange('yearBuilt', e.target.value)}
                className="w-full bg-slate-800 border border-slate-700 rounded-lg p-2 text-sm text-center"
              />
            </div>
          </div>

          <div>
            <label className="block text-xs font-medium text-slate-400 mb-1">MLS Public Remarks</label>
            <textarea 
              rows={4}
              value={adData.publicRemarks} 
              onChange={(e) => handleChange('publicRemarks', e.target.value)}
              className="w-full bg-slate-800 border border-slate-700 rounded-lg p-2.5 text-sm focus:border-indigo-500 focus:outline-none"
            />
          </div>
        </div>

        {/* RIGHT COLUMN: 2026 A.I. EFFECTS & AD GENERATOR CONTROLS */}
        <div className="lg:col-span-5 bg-slate-950 p-5 rounded-xl border border-slate-800 flex flex-col justify-between space-y-6">
          <div>
            <div className="flex items-center justify-between border-b border-slate-800 pb-3 mb-4">
              <h2 className="text-lg font-semibold text-slate-200 flex items-center gap-2">
                <Wand2 className="w-5 h-5 text-indigo-400" /> 2026 AI Effects & Ad Tools
              </h2>
            </div>

            {/* AI ACTION BUTTONS */}
            <div className="space-y-3">
              <button 
                onClick={generateAiCopy}
                disabled={isAiLoading}
                className="w-full flex items-center justify-center gap-2 py-3 px-4 bg-gradient-to-r from-blue-600 to-indigo-600 hover:from-blue-500 hover:to-indigo-500 text-white font-medium rounded-lg shadow-lg transition"
              >
                <Sparkles className="w-4 h-4" /> {isAiLoading ? 'Generating...' : '1-Click AI Copywriter & Hashtags'}
              </button>

              <button 
                onClick={triggerAiVisualEnhancements}
                className="w-full flex items-center justify-center gap-2 py-2.5 px-4 bg-slate-800 hover:bg-slate-700 text-slate-200 font-medium rounded-lg border border-slate-700 transition text-sm"
              >
                <ImageIcon className="w-4 h-4 text-sky-400" /> Apply AI Twilight & Virtual Staging
              </button>
            </div>

            {/* AI GENERATED PREVIEWS */}
            <div className="mt-6 space-y-4">
              <div>
                <label className="block text-xs font-medium text-indigo-400 mb-1">AI Ad Headline</label>
                <input 
                  type="text" 
                  value={adData.headline} 
                  onChange={(e) => handleChange('headline', e.target.value)}
                  placeholder="Click AI Copywriter to generate..."
                  className="w-full bg-slate-900 border border-slate-800 rounded-lg p-2 text-sm text-slate-100 font-medium"
                />
              </div>

              <div>
                <label className="block text-xs font-medium text-pink-400 mb-1 flex items-center gap-1">
                  <Video className="w-3.5 h-3.5" /> 2026 Short-Form Video Hook (Reels/TikTok)
                </label>
                <input 
                  type="text" 
                  value={adData.shortFormHook} 
                  onChange={(e) => handleChange('shortFormHook', e.target.value)}
                  placeholder="Generated spoken video hook..."
                  className="w-full bg-slate-900 border border-slate-800 rounded-lg p-2 text-sm text-pink-300 italic"
                />
              </div>

              <div>
                <label className="block text-xs font-medium text-indigo-400 mb-1">Social Media Post Body</label>
                <textarea 
                  rows={4}
                  value={adData.socialCaption} 
                  onChange={(e) => handleChange('socialCaption', e.target.value)}
                  placeholder="Generated social ad body copy..."
                  className="w-full bg-slate-900 border border-slate-800 rounded-lg p-2 text-sm text-slate-300"
                />
              </div>

              <div>
                <label className="block text-xs font-medium text-slate-400 mb-1">Hashtag Bank</label>
                <input 
                  type="text" 
                  value={adData.hashtags} 
                  onChange={(e) => handleChange('hashtags', e.target.value)}
                  placeholder="#JustListed #PropertyTour"
                  className="w-full bg-slate-900 border border-slate-800 rounded-lg p-2 text-xs text-blue-400"
                />
              </div>
            </div>
          </div>

          <button 
            onClick={() => alert('Ad Package Ready for Publishing!')}
            className="w-full flex items-center justify-center gap-2 py-3 bg-emerald-600 hover:bg-emerald-500 text-white font-semibold rounded-lg transition"
          >
            <Share2 className="w-4 h-4" /> Publish / Launch Campaign
          </button>
        </div>

      </div>
    </div>
  );
}
